# Questão 2 - Teste Estrutural

<p align="center">
  <img src="https://github.com/user-attachments/assets/fa10670a-a8a3-4d13-8fea-84656c8a156a" />
</p>

*Bloco de código utilizado para a questão*

## Resolução

### a) Utilizando o número das linhas para seguir a fluxo do código, seu grafo de fluxo de controle fica assim:
<p align="center">
  <img src="https://github.com/user-attachments/assets/3bf06582-5e60-43be-8197-4cb912c19e4f" />
</p>

### b) Conforme demonstrado na imagem abaixo existem 4 caminhos independentes neste código, sendo eles:

<p align="center">
  <img src="https://github.com/user-attachments/assets/62b47873-54b7-40d7-9500-52da06ac9a3d" />
</p>

### c) Lista de todos os caminhos independentes:

```
C1 = <18-20 4 5 6 22-24 25>
C2 = <18-20 4 5 7 9 10 11 22-24 25>
C3 = <18-20 4 5 7 9 10 12-13 9 10 11 22-24 25>
C4 = <18-20 4 5 7 9 15 21 25>
C5 = <18-20 4 5 7 9 10 12-13 9 15 21 25>
```

### d) Para cada um dos caminhos independentes segue a lógica de caso de teste:

C1: `int numero` deve ser igual ou menor que 0 (caso de teste: 0)\
C2: `int numero` deve ser qualquer inteiro par não primo maior que 4 (caso de teste: 4)\
C3: `int numero` deve ser qualquer inteiro ímpar não primo maior que 9 (caso de teste: 9)\
C4: `int numero` deve ser igual a 2 ou 3 (caso de teste: 2)\
C5: `int numero` deve ser um inteiro primo maior que 4 e menor que 9, ou seja, 5 ou 7 (caso de teste: 5)

*Obs.: a lógica dos valores descritos acima levou em consideração na maior parte dos casos a comparação realizada entre o `numero` e `i` já que o último se inicia em 2 e incrementa de 1 em 1 e é o pilar da criação da maior parte dos caminhos.*

### e) As seguintes condições estão presentes no código:

Condição de verificação de número primo:

```C
if (ehPrimo(numero))
```

Condição de invalidade de número primo:

```C
if (num <= 1) {
  return false;
}
```

Condição de número não primo:

```C
for (int i = 2; i * i <= num; i++) {
  if (num % i == 0) {
    return false;
  }
}
```

### f) Para uma cobertura mínima de casos de teste seria necessário:

Passar por todos os caminhos independentes, ou seja, utilizar tais valores que compõem todos os possíveis caminhos independentes, sendo assim, seria necessário testar o código com os valores: 0, 2, 4, 5, 9 para `int numero`. Dessa forma, garantimos que ao menos todos os casos estão sendo tratados, já que é impossível garantir para 100% dos casos, que significaria testar para todo o conjunto de entradas, que neste caso é o conjunto dos números inteiros.

### g) Para análise de valor limite consideraremos a seguinte tabela:

| Número   | Esperado |
| -------- | -------- |
| 1        | false    |
| 3        | true     |
| 4        | false    |
| 5        | true     |

* Para o primeiro caso iremos testar a primeira condição, onde o valor de `num` deve ser menor ou igual a 1, então, testamos para 1.
* Para o segundo, consideraremos a condição do loop que, inicialmente, compara `num` com 4, dessa forma, testamos no limite, onde `num` é menor que 4, então selecionamos 3.
* Para o terceiro, testamos a condição do loop também, mas para a outra extremidade, ou seja, `num` deve ser qualquer número maior ou igual a 4, neste caso testamos para 4.
* Para a quarta, testamos se o número cobre o limite do loop e ao mesmo tempo passa na extremidade da condição interna, ou seja, o número é primo e maior que 4, testamos então para 5.
