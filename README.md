# Autômato de Pilha (PDA) - Linguagem aⁿbⁿ

## Descrição

Este projeto implementa um **Autômato de Pilha (Pushdown Automaton - PDA)** em C++.

O programa possui um PDA padrão que reconhece a linguagem:

```text
L = { aⁿ bⁿ | n ≥ 1 }
```

Ou seja, aceita palavras que possuem a mesma quantidade de símbolos `a` seguidos da mesma quantidade de símbolos `b`.

Exemplos aceitos:

```text
ab
aabb
aaabbb
```

Exemplos rejeitados:

```text
aab
abb
ba
abab
```

---

# Requisitos

Para executar o projeto é necessário possuir:

* Compilador C++ com suporte a C++17
* MSYS2 UCRT64 (utilizado nos testes)

---

# Instalação do MSYS2

Baixe e instale o MSYS2:

https://www.msys2.org/

Após a instalação, abra o terminal:

```text
MSYS2 UCRT64
```

Instale o compilador C++:

```bash
pacman -S --needed mingw-w64-ucrt-x86_64-gcc
```

Verifique se a instalação foi concluída:

```bash
g++ --version
```

---

# Compilação

Salve o código como:

```text
automato_pilha.cpp
```

Acesse a pasta do projeto:

```bash
cd /c/Users/SEU_USUARIO/Downloads
```

Compile:

```bash
g++ -std=c++17 automato_pilha.cpp -o automato
```

Se não aparecer nenhuma mensagem de erro, a compilação foi realizada com sucesso.

---

# Execução

Execute o programa:

```bash
./automato.exe
```

Será exibido o menu:

```text
--- PDA: a^n b^n ---

1 - usar PDA padrao
2 - criar PDA personalizado
3 - testar uma palavra
4 - rodar testes padrao
0 - sair
```

---

# Teste Automático

Para verificar se o PDA está funcionando corretamente:

1. Execute o programa
2. Escolha a opção:

```text
4
```

O programa executará os testes pré-definidos.

Exemplo:

```text
ab: esperado=aceitar resultado=aceitar ok
aabb: esperado=aceitar resultado=aceitar ok
aaabbb: esperado=aceitar resultado=aceitar ok
eps: esperado=rejeitar resultado=rejeitar ok
a: esperado=rejeitar resultado=rejeitar ok
b: esperado=rejeitar resultado=rejeitar ok
ba: esperado=rejeitar resultado=rejeitar ok
aab: esperado=rejeitar resultado=rejeitar ok
abb: esperado=rejeitar resultado=rejeitar ok
abab: esperado=rejeitar resultado=rejeitar ok

10/10 testes passaram
```

---

# Teste Manual

Para testar palavras manualmente:

1. Execute o programa
2. Escolha a opção:

```text
3
```

3. Digite uma palavra.

Exemplo:

```text
Palavra: aabb
```

Saída:

```text
Processando "aabb"

(q0, aabb, Z)
(q0, abb, AZ)
(q0, bb, AAZ)
(q1, b, AZ)
(q1, eps, Z)
(q2, eps, Z)

-> ACEITO

ACEITO
```

---

# Criando um PDA Personalizado

Selecione a opção:

```text
2
```

Informe:

* Estado inicial
* Símbolo inicial da pilha
* Estados de aceitação
* Transições

Formato das transições:

```text
de simbolo topo para empilhar
```

Exemplo:

```text
q0 a Z q0 AZ
```

Símbolos especiais:

```text
eps -> transição vazia
-   -> não empilha nada
```

Exemplo:

```text
q1 b A q1 -
```

Para finalizar a inserção das transições, pressione ENTER em uma linha vazia.

---

# Estruturas Utilizadas

O projeto utiliza:

* vector
* stack
* tuple
* unordered_map
* stringstream

para representar:

* Estados do autômato
* Configurações instantâneas
* Pilha
* Função de transição
* Simulação não determinística
