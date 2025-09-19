<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Gerenciador de Tarefas</title>
</head>
<body>
  <script>
    function gerenciarTarefas(listaDeTarefas, acao) {
      if (acao === "adicionar") {
        let descricao = prompt("Insira uma descrição para a nova tarefa:");
        if (descricao && descricao.trim() !== "") {
          listaDeTarefas.push({ descricao: descricao.trim(), concluida: false });
          alert("Tarefa adicionada com sucesso!");
        } else {
          alert("Descrição inválida, tarefa não adicionada.");
        }
      } 
      else if (acao === "remover") {
        listaDeTarefas = listaDeTarefas.filter(tarefa => !tarefa.concluida);
        alert("Tarefas concluídas foram removidas!");
      } 
      else if (acao === "listar") {
        let pendentes = listaDeTarefas.filter(tarefa => !tarefa.concluida);
        if (pendentes.length === 0) {
          alert("Nenhuma tarefa pendente.");
        } else {
          let lista = "📌 Tarefas Pendentes:\n";
          pendentes.forEach((tarefa, i) => {
            lista += `${i + 1}. ${tarefa.descricao}\n`;
          });
          alert(lista);
        }
      }
      return listaDeTarefas;
    }

    // Lista inicial de tarefas
    let tarefas = [
      { descricao: "Estudar", concluida: false },
      { descricao: "Fazer exercícios", concluida: false },
      { descricao: "Trabalhar", concluida: false },
      { descricao: "Lavar a louça", concluida: true }
    ];

    // Exemplos de uso
    tarefas = gerenciarTarefas(tarefas, "listar");   // Lista tarefas pendentes
    tarefas = gerenciarTarefas(tarefas, "adicionar");// Adiciona nova tarefa
    tarefas = gerenciarTarefas(tarefas, "remover");  // Remove concluídas
    tarefas = gerenciarTarefas(tarefas, "listar");   // Lista novamente
  </script>
</body>
</html>
