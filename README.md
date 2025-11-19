import 'package:flutter/material.dart';
import 'package:http/http.dart' as http;
import 'dart:convert';
import 'package:shared_preferences/shared_preferences.dart';

const String baseUrl = "https://vida-equilibrio-api-69a356625afd.herokuapp.com";

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      title: "GS Flutter",
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: const UserIdGate(),
    );
  }
}

///
/// 1) TELA QUE DECIDE SE PRECISA PEGAR USERID OU ENTRA DIRETO
///
class UserIdGate extends StatefulWidget {
  const UserIdGate({super.key});

  @override
  State<UserIdGate> createState() => _UserIdGateState();
}

class _UserIdGateState extends State<UserIdGate> {
  String? savedId;

  @override
  void initState() {
    super.initState();
    _loadId();
  }

  Future<void> _loadId() async {
    final prefs = await SharedPreferences.getInstance();
    final id = prefs.getString("userId");

    setState(() {
      savedId = id;
    });
  }

  @override
  Widget build(BuildContext context) {
    if (savedId == null) {
      return UserIdForm(
        onSaved: () {
          _loadId();
        },
      );
    } else {
      return ActivitiesPage(userId: savedId!);
    }
  }
}

///
/// 2) TELA DE DIGITAR USERID
///
class UserIdForm extends StatefulWidget {
  final VoidCallback onSaved;

  const UserIdForm({super.key, required this.onSaved});

  @override
  State<UserIdForm> createState() => _UserIdFormState();
}

class _UserIdFormState extends State<UserIdForm> {
  final controller = TextEditingController();

  Future<void> _save() async {
    if (controller.text.trim().isEmpty) return;

    final prefs = await SharedPreferences.getInstance();
    await prefs.setString("userId", controller.text.trim());

    widget.onSaved();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text("Identificação")),
      body: Padding(
        padding: const EdgeInsets.all(20),
        child: Column(
          children: [
            TextField(
              controller: controller,
              decoration: const InputDecoration(
                labelText: "Digite seu userId",
              ),
            ),
            const SizedBox(height: 20),
            ElevatedButton(
              onPressed: _save,
              child: const Text("Continuar"),
            ),
          ],
        ),
      ),
    );
  }
}

///
/// 3) TELA PRINCIPAL — LISTA DE ATIVIDADES (GET /atividades)
///
class ActivitiesPage extends StatefulWidget {
  final String userId;

  const ActivitiesPage({super.key, required this.userId});

  @override
  State<ActivitiesPage> createState() => _ActivitiesPageState();
}

class _ActivitiesPageState extends State<ActivitiesPage> {
  List<dynamic> lista = [];

  @override
  void initState() {
    super.initState();
    _fetchAtividades();
  }

  Future<void> _fetchAtividades() async {
    try {
      final url = Uri.parse("$baseUrl/atividades");
      final resp = await http.get(url);

      if (resp.statusCode == 200) {
        setState(() {
          lista = jsonDecode(resp.body);
        });

        ScaffoldMessenger.of(context).showSnackBar(
          const SnackBar(content: Text("Atividades carregadas")),
        );
      } else {
        throw Exception("Erro");
      }
    } catch (e) {
      ScaffoldMessenger.of(context).showSnackBar(
        const SnackBar(content: Text("Falha ao carregar")),
      );
    }
  }

  Future<void> _trocarUserId() async {
    final prefs = await SharedPreferences.getInstance();
    await prefs.remove("userId");

    Navigator.pushReplacement(
      context,
      MaterialPageRoute(builder: (_) => const UserIdGate()),
    );
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text("Todas atividades"),
        actions: [
          IconButton(
            onPressed: _trocarUserId,
            icon: const Icon(Icons.person),
          )
        ],
      ),
      body: ListView.builder(
        itemCount: lista.length,
        itemBuilder: (_, i) {
          final item = lista[i];
          return ListTile(
            title: Text(item["titulo"] ?? "Sem título"),
            subtitle: Text(item["descricao"] ?? ""),
            onTap: () {
              Navigator.push(
                context,
                MaterialPageRoute(
                  builder: (_) => DetalhePage(
                    id: item["id"].toString(),
                    userId: widget.userId,
                  ),
                ),
              );
            },
          );
        },
      ),
    );
  }
}

///
/// 4) DETALHE DA ATIVIDADE (GET /atividades/{id}?nome=)
///
class DetalhePage extends StatefulWidget {
  final String id;
  final String userId;

  const DetalhePage({
    super.key,
    required this.id,
    required this.userId,
  });

  @override
  State<DetalhePage> createState() => _DetalhePageState();
}

class _DetalhePageState extends State<DetalhePage> {
  Map<String, dynamic>? atividade;
  List<String> joined = [];

  @override
  void initState() {
    super.initState();
    _carregarDetalhe();
    _carregarParticipacoes();
  }

  Future<void> _carregarParticipacoes() async {
    final prefs = await SharedPreferences.getInstance();
    joined = prefs.getStringList("joinedActivities") ?? [];
    setState(() {});
  }

  Future<void> _salvarParticipacoes() async {
    final prefs = await SharedPreferences.getInstance();
    await prefs.setStringList("joinedActivities", joined);
  }

  Future<void> _carregarDetalhe() async {
    try {
      final url = Uri.parse(
        "$baseUrl/atividades/${widget.id}?nome=${widget.userId}",
      );

      final resp = await http.get(url);

      if (resp.statusCode == 200) {
        setState(() {
          atividade = jsonDecode(resp.body);
        });
      } else {
        throw Exception("erro");
      }
    } catch (e) {
      ScaffoldMessenger.of(context).showSnackBar(
        const SnackBar(content: Text("Erro ao carregar detalhe")),
      );
    }
  }

  bool get participa => joined.contains(widget.id);

  Future<void> _toggleParticipacao() async {
    if (participa) {
      joined.remove(widget.id);
      ScaffoldMessenger.of(context).showSnackBar(
        const SnackBar(content: Text("Você saiu da atividade")),
      );
    } else {
      joined.add(widget.id);
      ScaffoldMessenger.of(context).showSnackBar(
        const SnackBar(content: Text("Você entrou na atividade")),
      );
    }

    await _salvarParticipacoes();
    setState(() {});
  }

  @override
  Widget build(BuildContext context) {
    if (atividade == null) {
      return Scaffold(
        appBar: AppBar(),
        body: const Center(child: CircularProgressIndicator()),
      );
    }

    return Scaffold(
      appBar: AppBar(title: Text(atividade!["titulo"] ?? "Detalhes")),
      body: Padding(
        padding: const EdgeInsets.all(20),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            Text(
              atividade!["titulo"] ?? "",
              style: const TextStyle(
                fontSize: 22,
                fontWeight: FontWeight.bold,
              ),
            ),
            const SizedBox(height: 10),
            Text(atividade!["descricao"] ?? ""),
            const SizedBox(height: 20),
            ElevatedButton(
              onPressed: _toggleParticipacao,
              child: Text(participa ? "Sair" : "Se juntar"),
            )
          ],
        ),
      ),
    );
  }
}