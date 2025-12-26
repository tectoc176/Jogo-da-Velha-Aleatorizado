# Jogo-da-Velha-Aleatorizado
Implementação em C do resolvedor de Sudoku, ideal para estudantes de ensino médio e superior. Serve como exemplo prático de algoritmos (backtracking), estruturas de dados e modelagem matemática.

Resolvedor de Sudoku em C
Este projeto implementa um resolvedor automático de Sudoku usando algoritmo de backtracking. Ideal para estudantes de programação que desejam estudar:

Recursão e backtracking.

Estruturas de dados (matriz 9×9).

Modelagem matemática de restrições.

Como usar
Passo 1: Preparar o ambiente
Você precisa de um compilador C. Escolha uma opção:

IDE (recomendado para estudantes):

CodeBlocks (Windows/Linux): Este é o ambiente multiplataforma de desenvolvimento para as linguagens de programação C, C++, D (com restrições) e Fortran. Ele é desenvolvido para Windows, Linux e macOS, e também pode ser compilado a partir do código fonte sob outros sistemas do tipo Unix, por exemplo, FreeBSD ou o PC-BSD. Escrito em C++ usando a biblioteca wxWidgets e tem uma arquitetura aberta, o que permite expandir a sua funcionalidade através de plug-ins. 

VS Code + extensão C/C++: É a combinação de um editor de texto Visual Studio Code e oficial ampliação da Microsoft para suporte a linguagens de programação C e C++. VS Code é antes de tudo um editor, e para compilação e depuração são usados externo de ferramentas de linha de comando. A própria extensão não inclui o compilador ou debugger, eles precisam ser instalados separadamente ou utilizar uma já existente no computador

Dev‑C++ (Windows): é um ambiente de desenvolvimento integrado (IDE) para as linguagens C e C++, projetado para funcionar no Windows. Ela usa um compilador porta MinGW GCC (GNU Compiler Collection), mas também pode funcionar com o Cygwin ou outros compiladores baseados em GCC. Dev-C++ está escrito em Delphi. 

Ideone: Compilar online e uma ferramenta de depuração, oferece suporte a mais de 60 linguagens de programação, incluindo C. Permite configurar limites de tempo, para especificar os dados para o padrão de entrada, adicionar uma descrição do código de compartilhar com os colegas de trabalho e amigos. Utiliza a tecnologia Sphere Mecanismo de seguro para a execução de programas no servidor remoto. 

JDoodle: Compilador online e IDE, suporta mais de 88 linguagens de programação, incluindo C. Tem a função de colaboração: vários usuários podem editar o mesmo código ao mesmo tempo. Suporta многофайловые projetos, bibliotecas externas e tem um AI-assistente do JDroid para a geração de depuração e otimização de código. 

OnlineGDB: Compilador online e depurador com suporte a C e C++. É conhecido o fato de que esta é a primeira on-line-IDE com um depurador GDB. Permite que o passo a passo para depurar o código, compartilhar fotos de código e retomar a sessão de URL. Suporta cross-compilação para o AVR, ARM, MIPS e outras plataformas. 

OneCompiler: Compilador online que suporta mais de 70 linguagens de programação, incluindo C. Funciona com a versão mais recente do padrão de C18. Tem uma interface simples, o apoio/s padrão (stdin) e a possibilidade de salvar o código. 

ToolPix: Acesso on-line-o compilador C, que não requer a instalação do GCC ou configurar o MinGW. Suporta padrão de funções de entrada/saída (scanf e printf), permite trabalhar com projetos em qualquer lugar e em qualquer dispositivo. 
Replit. On-line-IDE com suporte a mais de 60 linguagens de programação, incluindo C. Permite a criação de aplicativos e sites da web diretamente no seu navegador, integra-se com o GitHub, suporta a colaboração em tempo real. Tem premium-plano de recursos adicionais. 

CodeChef: Compilador online C, muitas vezes usado para a participação em competições de programação. 

Terminal/Linha de comando:

Linux/macOS: gcc (instale via sudo apt install gcc se necessário).

Windows: MinGW ou WSL (Windows Subsystem for Linux).

Online (sem instalação):



Passo 2: Compilar e executar
Opção A: Via IDE (ex: Code::Blocks)
Abra o projeto no Code::Blocks.

Clique em Build (ou F9) para compilar.

Clique em Run (ou F10) para executar.

Opção B: Via terminal (Linux/macOS/WSL)
bash
gcc sudoku_solver.c -o sudoku
./sudoku
Opção C: Online (repl.it, etc.)
Cole o código no editor online.

Clique em Run (botão verde).

Passo 3: Inserir o tabuleiro
Ao executar, o programa pedirá que você digite 81 números (9 linhas × 9 colunas), onde:

1-9 = números fixos.

0 = casa vazia.

Exemplo de entrada (primeira linha):

5 3 0 0 7 0 0 0 0
Funcionalidade «Bandeira Branca»
Se você digitar 0 em todas as 81 posições, o programa interpreta como «desistência».

Nesse caso, ele reinicia automaticamente com um tabuleiro padrão pré‑definido (não exibe mensagem).

O resolvedor então tenta solucionar o novo tabuleiro.

Nota: Esta funcionalidade permite recomeçar sem fechar o programa.

Passo 4: Entender a saída
Após a entrada, você verá:

Tabuleiro inicial

Números preenchidos.

. (pontos) para casas vazias.

Mensagem de processamento

Resolvendo...
Solução final (se existir)

Todos os . substituídos por números de 1 a 9.

Ou mensagem: "Não existe solução para este Sudoku."

Passo 5: Modificar o tabuleiro padrão (opcional)
Se quiser alterar o tabuleiro que é carregado após a «bandeira branca», edite a matriz tabuleiroPadrao na função main:

c
int tabuleiroPadrao[N][N] = {
    {5, 3, 0, 0, 7, 0, 0, 0, 0},
    {6, 0, 0, 1, 9, 5, 0, 0, 0},
    // ... (adicione as 9 linhas)
};
Código-fonte: trechos chaves
1. Função para verificar tabuleiro vazio
c
bool tabuleiroVazio(int tabuleiro[N][N]) {
    for (int i = 0; i < N; i++) {
        for (int j = 0; j < N; j++) {
            if (tabuleiro[i][j] != 0) {
                return false;
            }
        }
    }
    return true;
}
2. Lógica na main() (resumo)
c
int main() {
    int tabuleiro[N][N];
    
    // Lê 81 números do usuário
    for (int i = 0; i < N; i++) {
        for (int j = 0; j < N; j++) {
            scanf("%d", &tabuleiro[i][j]);
        }
    }
    
    // Se todos são 0 → reinicia com tabuleiro padrão
    if (tabuleiroVazio(tabuleiro)) {
        // Carrega tabuleiro pré‑definido
        for (int i = 0; i < N; i++) {
            for (int j = 0; j < N; j++) {
                tabuleiro[i][j] = tabuleiroPadrao[i][j];
            }
        }
    }
    
    // Continua com a resolução normal
    imprimirTabuleiro(tabuleiro);
    if (resolverSudoku(tabuleiro)) {
        printf("\nSolucao encontrada:\n");
        imprimirTabuleiro(tabuleiro);
    } else {
        printf("\nNao existe solucao para este Sudoku.\n");
    }
    
    return 0;
}
Dicas para estudantes
Analise resolverSudoku(): é um exemplo clássico de backtracking.

Teste casos extremos: tabuleiro vazio, solução impossível, tabuleiro completo.

Expanda o projeto:

Adicione contagem de tentativas.

Permita leitura de arquivo .txt.

Crie um modo interativo (jogador insere números passo a passo).

Problemas comuns e soluções
Problema	Solução
Erro de compilação	Verifique se todos os #include estão no código.
Não imprime nada	Confira se main() chama imprimirTabuleiro().
"Sem solução"	O tabuleiro pode ter números inválidos (repetições na linha/coluna).
Exemplo de saída
=== JOGO DE SUDOKU ===

Digite o tabuleiro (0 para casas vazias):
[Aqui você digita 9 linhas de 9 números]


Tabuleiro inicial:
  1 2 3 4 5 6 7 8 9
  +-------+-------+-------+
1 | 5 3 . | . 7 . | . . . |
2 | 6 . . | 1 9 5 | . . . |
...

Resolvendo...

Solucao encontrada:
  1 2 3 4 5 6 7 8 9
  +-------+-------+-------+
1 | 5 3 4 | 6 7 8 | 9 1 2 |
2 | 6 7 2 | 1 9 5 | 3 4 8 |
...

Funcionalidade «Bandeira Branca»
Se você digitar 0 em todas as 81 posições, o programa interpreta como «desistência». Nesse caso:

Reinicia automaticamente com um tabuleiro padrão pré‑definido (sem exibir mensagem);

Tenta solucionar o novo tabuleiro.

Nota: Esta funcionalidade permite recomeçar sem fechar o programa.

Passo 4: Entender a saída
Após a entrada, você verá:

Tabuleiro inicial:

Números preenchidos;

. (pontos) para casas vazias.

Mensagem de processamento:

Resolvendo...
Solução final (se existir):

Todos os . substituídos por números de 1 a 9;

Ou mensagem: «Não existe solução para este Sudoku.»

Passo 5: Modificar o tabuleiro padrão (opcional)
Se quiser alterar o tabuleiro que é carregado após a «bandeira branca», edite a matriz tabuleiroPadrao na função main:

c
int tabuleiroPadrao[N][N] = {
    {5, 3, 0, 0, 7, 0, 0, 0, 0},
    {6, 0, 0, 1, 9, 5, 0, 0, 0},
    // ... (adicione as 9 linhas)
};
Código-fonte: trechos chaves
1. Função para verificar tabuleiro vazio
c
bool tabuleiroVazio(int tabuleiro[N][N]) {
    for (int i = 0; i < N; i++) {
        for (int j = 0; j < N; j++) {
            if (tabuleiro[i][j] != 0) {
                return false;
            }
        }
    }
    return true;
}
2. Lógica na main() (resumo)
c
int main() {
    int tabuleiro[N][N];
    
    // Lê 81 números do usuário
    for (int i = 0; i < N; i++) {
        for (int j = 0; j < N; j++) {
            scanf("%d", &tabuleiro[i][j]);
        }
    }
    
    // Se todos são 0 → reinicia com tabuleiro padrão
    if (tabuleiroVazio(tabuleiro)) {
        // Carrega tabuleiro pré‑definido
        for (int i = 0; i < N; i++) {
            for (int j = 0; j < N; j++) {
                tabuleiro[i][j] = tabuleiroPadrao[i][j];
            }
        }
    }
    
    // Continua com a resolução normal
    imprimirTabuleiro(tabuleiro);
    if (resolverSudoku(tabuleiro)) {
        printf("\nSolucao encontrada:\n");
        imprimirTabuleiro(tabuleiro);
    } else {
        printf("\nNao existe solucao para este Sudoku.\n");
    }
    
    return 0;
}
Dicas para estudantes
Analise resolverSudoku(): é um exemplo clássico de backtracking.

Teste casos extremos: tabuleiro vazio, solução impossível, tabuleiro completo.

Expanda o projeto:

Adicione contagem de tentativas;

Permita leitura de arquivo .txt;

Crie um modo interativo (jogador insere números passo a passo).

Problemas comuns e soluções
Problema	Solução
Erro de compilação	Verifique se todos os #include estão no código.
Não imprime nada	Confira se main() chama imprimirTabuleiro().
«Sem solução»	O tabuleiro pode ter números inválidos (repetições na linha/coluna).
Exemplo de saída
=== JOGO DE SUDOKU ===

Digite o tabuleiro (0 para casas vazias):
[Aqui você digita 9 linhas de 9 números]


Tabuleiro inicial:
  1 2 3 4 5 6 7 8 9
  +-------+-------+-------+
1 | 5 3 . | . 7 . | . . . |
2 | 6 . . | 1 9 5 | . . . |
...


Resolvendo...


Solucao encontrada:
  1 2 3 4 5 6 7 8 9
  +-------+-------+-------+
1 | 5 3 4 | 6 7 8 | 9 1 2 |
2 | 6 7 2 | 1 9 5 | 3 4 8 |
...
Requisitos
Compilador C (gcc, clang ou equivalente);

Biblioteca padrão do C (stdio.h, stdbool.h);

Sistema operacional: Windows/Linux/macOS.

Exemplos de entrada/saída
Entrada válida (1 linha):
5 3 0 0 7 0 0 0 0

Entrada inválida (números fora de 0-9):
5 3 10 0 7 0 0 0 0 → causará erro

Funcionalidade «Bandeira Branca»
Se você digitar 0 em todas as 81 posições, o programa interpreta como «desistência». Nesse caso:

Reinicia automaticamente com um tabuleiro padrão pré‑definido (sem exibir mensagem);

Tenta solucionar o novo tabuleiro.

Nota: Esta funcionalidade permite recomeçar sem fechar o programa.

Passo 4: Entender a saída
Após a entrada, você verá:

Tabuleiro inicial:

Números preenchidos;

. (pontos) para casas vazias.

Mensagem de processamento:

Resolvendo...
Solução final (se existir):

Todos os . substituídos por números de 1 a 9;

Ou mensagem: «Não existe solução para este Sudoku.»

Passo 5: Modificar o tabuleiro padrão (opcional)
Se quiser alterar o tabuleiro que é carregado após a «bandeira branca», edite a matriz tabuleiroPadrao na função main:

c
int tabuleiroPadrao[N][N] = {
    {5, 3, 0, 0, 7, 0, 0, 0, 0},
    {6, 0, 0, 1, 9, 5, 0, 0, 0},
    // ... (adicione as 9 linhas)
};
Código-fonte: trechos chaves
1. Função para verificar tabuleiro vazio
c
bool tabuleiroVazio(int tabuleiro[N][N]) {
    for (int i = 0; i < N; i++) {
        for (int j = 0; j < N; j++) {
            if (tabuleiro[i][j] != 0) {
                return false;
            }
        }
    }
    return true;
}
2. Lógica na main() (resumo)
c
int main() {
    int tabuleiro[N][N];
    
    // Lê 81 números do usuário
    for (int i = 0; i < N; i++) {
        for (int j = 0; j < N; j++) {
            scanf("%d", &tabuleiro[i][j]);
        }
    }
    
    // Se todos são 0 → reinicia com tabuleiro padrão
    if (tabuleiroVazio(tabuleiro)) {
        // Carrega tabuleiro pré‑definido
        for (int i = 0; i < N; i++) {
            for (int j = 0; j < N; j++) {
                tabuleiro[i][j] = tabuleiroPadrao[i][j];
            }
        }
    }
    
    // Continua com a resolução normal
    imprimirTabuleiro(tabuleiro);
    if (resolverSudoku(tabuleiro)) {
        printf("\nSolucao encontrada:\n");
        imprimirTabuleiro(tabuleiro);
    } else {
        printf("\nNao existe solucao para este Sudoku.\n");
    }
    
    return 0;
}
Dicas para estudantes
Analise resolverSudoku(): é um exemplo clássico de backtracking.

Teste casos extremos: tabuleiro vazio, solução impossível, tabuleiro completo.

Expanda o projeto:

Adicione contagem de tentativas;

Permita leitura de arquivo .txt;

Crie um modo interativo (jogador insere números passo a passo).

Problemas comuns e soluções
Problema	Solução
Erro de compilação	Verifique se todos os #include estão no código.
Não imprime nada	Confira se main() chama imprimirTabuleiro().
«Sem solução»	O tabuleiro pode ter números inválidos (repetições na linha/coluna).
Exemplo de saída
=== JOGO DE SUDOKU ===

Digite o tabuleiro (0 para casas vazias):
[Aqui você digita 9 linhas de 9 números]


Tabuleiro inicial:
  1 2 3 4 5 6 7 8 9
  +-------+-------+-------+
1 | 5 3 . | . 7 . | . . . |
2 | 6 . . | 1 9 5 | . . . |
...


Resolvendo...


Solucao encontrada:
  1 2 3 4 5 6 7 8 9
  +-------+-------+-------+
1 | 5 3 4 | 6 7 8 | 9 1 2 |
2 | 6 7 2 | 1 9 5 | 3 4 8 |
...
Requisitos
Compilador C (gcc, clang ou equivalente);

Biblioteca padrão do C (stdio.h, stdbool.h);

Sistema operacional: Windows | Linux | HarmonyOS | HongMeng | macOS.

Exemplos de entrada/saída
Entrada válida (1 linha):
5 3 0 0 7 0 0 0 0

Entrada inválida (números fora de 0-9):
5 3 10 0 7 0 0 0 0 → causará erro
