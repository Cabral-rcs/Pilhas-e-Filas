# Pilhas-e-Filas

``` javascript
const prompt = require('prompt-sync')();

// Classe para implementar a Fila (FIFO)
class FilaAtendimento {
  constructor() {
    this.alunos = [];
  }

  // Adicionar aluno à fila
  adicionarAluno(nome) {
    this.alunos.push(nome);
    console.log(`Aluno ${nome} adicionado à fila de atendimento.`);
  }

  // Remover (atender) o primeiro aluno da fila
  atenderAluno() {
    if (this.alunos.length === 0) {
      console.log("Não há alunos na fila para atender.");
      return null;
    }
    const alunoAtendido = this.alunos.shift();
    console.log(`Aluno ${alunoAtendido} atendido.`);
    return alunoAtendido;
  }

  // Visualizar quem será o próximo a ser atendido
  verProximoAluno() {
    if (this.alunos.length === 0) {
      console.log("Não há alunos na fila.");
      return null;
    }
    const proximo = this.alunos[0];
    console.log(`Próximo aluno a ser atendido: ${proximo}`);
    return proximo;
  }

  // Mostrar todos os alunos na fila
  mostrarFila() {
    if (this.alunos.length === 0) {
      console.log("A fila de atendimento está vazia.");
      return;
    }
    console.log("Fila de Atendimento:");
    this.alunos.forEach((aluno, index) => {
      console.log(`${index + 1}. ${aluno}`);
    });
  }
}

// Classe para implementar a Pilha (LIFO)
class PilhaDocumentos {
  constructor() {
    this.documentos = [];
  }

  // Adicionar documento urgente à pilha
  adicionarDocumento(descricao) {
    this.documentos.push(descricao);
    console.log(`Documento "${descricao}" adicionado à pilha de documentos urgentes.`);
  }

  // Remover (resolver) o documento no topo da pilha
  resolverDocumento() {
    if (this.documentos.length === 0) {
      console.log("Não há documentos para resolver.");
      return null;
    }
    const documentoResolvido = this.documentos.pop();
    console.log(`Documento "${documentoResolvido}" resolvido.`);
    return documentoResolvido;
  }

  // Visualizar o documento no topo da pilha
  verTopoDocumento() {
    if (this.documentos.length === 0) {
      console.log("Não há documentos na pilha.");
      return null;
    }
    const topo = this.documentos[this.documentos.length - 1];
    console.log(`Documento no topo: "${topo}"`);
    return topo;
  }

  // Mostrar todos os documentos pendentes
  mostrarDocumentos() {
    if (this.documentos.length === 0) {
      console.log("A pilha de documentos está vazia.");
      return;
    }
    console.log("Documentos Pendentes (do mais recente ao mais antigo):");
    for (let i = this.documentos.length - 1; i >= 0; i--) {
      console.log(`${this.documentos.length - i}. ${this.documentos[i]}`);
    }
  }
}

// Função principal para interação com o usuário
function main() {
  const filaAtendimento = new FilaAtendimento();
  const pilhaDocumentos = new PilhaDocumentos();

  console.log("Sistema de Atendimento Escolar");

  while (true) {
    console.log("\nMenu:");
    console.log("1 - Adicionar aluno à fila");
    console.log("2 - Atender aluno");
    console.log("3 - Ver próximo aluno");
    console.log("4 - Mostrar fila");
    console.log("5 - Adicionar documento");
    console.log("6 - Resolver documento");
    console.log("7 - Ver documento no topo");
    console.log("8 - Mostrar documentos");
    console.log("9 - Sair");

    const opcao = prompt("Escolha uma opção: ");

    switch (opcao) {
      case '1':
        const nomeAluno = prompt("Digite o nome do aluno: ");
        filaAtendimento.adicionarAluno(nomeAluno);
        break;
      case '2':
        filaAtendimento.atenderAluno();
        break;
      case '3':
        filaAtendimento.verProximoAluno();
        break;
      case '4':
        filaAtendimento.mostrarFila();
        break;
      case '5':
        const descDocumento = prompt("Digite a descrição do documento: ");
        pilhaDocumentos.adicionarDocumento(descDocumento);
        break;
      case '6':
        pilhaDocumentos.resolverDocumento();
        break;
      case '7':
        pilhaDocumentos.verTopoDocumento();
        break;
      case '8':
        pilhaDocumentos.mostrarDocumentos();
        break;
      case '9':
        console.log("\nEstado final do sistema:");
        console.log("\nFila de Atendimento:");
        filaAtendimento.mostrarFila();
        console.log("\nPilha de Documentos:");
        pilhaDocumentos.mostrarDocumentos();
        console.log("\nEncerrando o sistema...");
        return;
      default:
        console.log("Opção inválida. Por favor, escolha uma opção de 1 a 9.");
    }
  }
}

main();
```
