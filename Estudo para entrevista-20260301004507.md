# Estudo para entrevista

# 🧠 Plano de Estudos — Estruturas de Dados & Algoritmos
* * *
# 1️⃣ Manipulação de Arrays
## 🔹 Inverter Array (In-place)
**Problema:**
Inverter um array sem criar outro array auxiliar.
**Entrada**

```cs

[1,2,3,4,5]


```

**Saída**

```cs

[5,4,3,2,1]


```

**Solução (Two Pointers)**

```php

let array = [1,2,3,4,5]

let left = 0;
let right = array.length - 1;

while (left < right) {
  const temp = array[left];
  array[left] = array[right];
  array[right] = temp;

  left++;
  right--;
}

console.log(array);


```

### 🎯 Complexidade
*   **Tempo:** O(n)
*   **Espaço:** O(1)
### ❓ Perguntas de Entrevista
*   Qual a complexidade?
*   Por que é melhor que criar outro array?
*   O que é complexidade de espaço?
**Resposta:**
Complexidade de espaço mede a memória extra utilizada além da entrada original.
Aqui usamos apenas uma variável temporária → **O(1)**.
* * *
## 🔹 Remover Duplicados (Array NÃO Ordenado)
**Entrada**

```cs

[4,2,7,4,8,2,9]


```

**Saída**

```cs

[4,2,7,8,9]


```

### ❌ Solução O(n²)

```php

let array = [4,2,7,4,8,2,9,9,8,1]
const helper = [array[0]]

for (var i = 0; i < array.length; i++){
  for (var j = 0; j < helper.length; j++){
    if(array[i] == helper[j]){
      break
    }
    if((j+1) == helper.length){
      helper.push(array[i])
    }
  }
}

console.log(helper)


```

**Complexidade:** O(n²)
* * *
### ✅ Solução O(n) usando HashMap

```php

let array = [4,2,7,4,8,2,9,9,8,1]

const seen = {}
const result = []

for (let i = 0; i < array.length; i++) {
  if (!seen[array[i]]) {
    seen[array[i]] = true
    result.push(array[i])
  }
}

console.log(result)


```

### 🎯 Complexidade
*   **Tempo:** O(n)
*   **Espaço:** O(n)
### ❓ Perguntas
*   Como manter a ordem original?
*   → Inserindo no `result` apenas na primeira aparição.
*   Qual estrutura usar?
*   → HashMap / Objeto.
* * *
## 🔹 Encontrar Maior e Menor (1 passada)
**Entrada**

```cs

[3,7,2,9,4,1]


```

**Saída**

```erlang

min = 1
max = 9



let array = [3,7,2,9,4,1, -1, 1010101]

let maior = array[0]
let menor = array[0]

for (let i = 0; i < array.length; i++) {
  if (maior < array[i]) {
    maior = array[i]
  }
  if (menor > array[i]) {
    menor = array[i]
  }
}

console.log(maior)
console.log(menor)


```

### 🎯 Complexidade
*   **Tempo:** O(n)
*   **Espaço:** O(1)
### ❓ Dá para fazer melhor que O(n)?
Não.
Você precisa olhar todos os elementos pelo menos uma vez.
* * *
## 🔹 Rotacionar Array (In-place)
**Problema:** Rotacionar para direita k posições.
**Entrada**

```cs

[1,2,3,4,5,6,7]
k = 3


```

**Saída**

```cs

[5,6,7,1,2,3,4]


```

### 💡 Solução Ótima (Reverse Trick)

```php

function rotateRight(array, k) {
  const n = array.length
  if (n === 0) return array

  k = k % n

  function reverse(start, end) {
    while (start < end) {
      const temp = array[start]
      array[start] = array[end]
      array[end] = temp
      start++
      end--
    }
  }

  // 1. Inverte tudo
  reverse(0, n - 1)

  // 2. Inverte primeiros k
  reverse(0, k - 1)

  // 3. Inverte restante
  reverse(k, n - 1)

  return array
}

console.log(rotateRight([1,2,3,4,5,6,7], 3))


```

### ❓ Como tratar k > n?

```erlang

k = k % n


```

### 🎯 Complexidade
*   **Tempo:** O(n)
*   **Espaço:** O(1)
* * *
## 🔹 Two Pointers — Soma Alvo
**Entrada**

```cs

[1,3,4,6,8,10]
target = 10


```

**Saída**

```php

4 e 6



let array = [1,3,4,6,8,10]
const target = 10

let left = 0
let right = array.length - 1

while (left < right) {
  const sum = array[left] + array[right]

  if (sum === target) {
    console.log(array[left], array[right])
    break
  }

  if (sum > target) {
    right--
  } else {
    left++
  }
}


```

### 🎯 Complexidade
*   **Tempo:** O(n)
*   **Espaço:** O(1)
* * *
# 2️⃣ Strings
## 🔹 Verificar Palíndromo
*   Two pointers
*   Ignorar espaços e caracteres especiais
*   O(n)
## 🔹 Anagrama
*   Comparar frequência de caracteres
*   HashMap
*   O(n)
## 🔹 Contar Frequência
*   Usar objeto `{}`
## 🔹 Substring mais longa sem repetição
*   Sliding Window
*   HashMap
*   O(n)
* * *
# 3️⃣ HashMap / Dicionário (MUUUUITO IMPORTANTE)
Use para:
*   Contagem de frequência
*   Detectar duplicados
*   Resolver problemas em O(n) ao invés de O(n²)
*   Lookup em O(1)
Se dominar HashMap → já sai na frente.
* * *
# 4️⃣ Complexidade (Big-O)

| Complexidade | Significado |
| ---| --- |
| O(1) | Constante |
| O(log n) | Busca binária |
| O(n) | Loop simples |
| O(n log n) | Ordenações eficientes |
| O(n²) | Dois loops aninhados |

Você precisa:
*   Identificar rapidamente
*   Justificar sua resposta
*   Comparar soluções
* * *
# 5️⃣ Recursão
*   Fatorial
*   Fibonacci
*   Backtracking básico
Entender:
*   Caso base
*   Pilha de chamadas
*   Complexidade exponencial
* * *
# 6️⃣ Stack (Pilha)
*   Parênteses válidos
*   Undo / Redo
*   Avaliar expressões
* * *
# 7️⃣ Queue (Fila)
*   BFS
*   Processamento em ordem
* * *
# 8️⃣ Dois Ponteiros
Muito comum em entrevista:
*   Soma alvo
*   Palíndromo
*   Remover duplicados ordenados
* * *
# 9️⃣ Busca Binária
*   Encontrar elemento
*   Encontrar posição de inserção
Complexidade:
*   O(log n)
* * *
# 🔟 Ordenação
Saber:
*   Quando usar `.sort()`
*   Conceito de:
    *   Quicksort
    *   Mergesort
* * *
# 1️⃣1️⃣ Sliding Window
*   Subarray com soma X
*   Maior substring sem repetição
Complexidade ideal:
*   O(n)
* * *
# 1️⃣2️⃣ Backend — Conceitos que CAEM MUITO
Como backend dev (seu caso 👀):
*   Normalização
*   Idempotência
*   Paginação
*   Race condition
*   Consistência vs Disponibilidade (CAP)

*   Questão 1 (Verificar Palíndromo\_
    
    🎯 Problema
    
    Verifique se uma string é palíndromo.
    
    Entrada
    
    ```bash
    
    "arara"
    
    
    ```
    
    Saída
    
    ```bash
    
    true
    
    
    ```
    
    Regras
    
    *   Ignore espaços
    *   Ignore maiúsculas/minúsculas
    *   Não use `reverse()`
    
    Extra (nível médio)
    
    A string pode conter pontuação:
    
    ```bash
    
    "A man, a plan, a canal: Panama"
    ```
    
    RESOLUÇÂO
    
    ```bash
    function ePalindromo(str) {
      // 1. Normalizamos para minúsculo
      str = str.toLowerCase();
    
      let esquerda = 0;
      let direita = str.length - 1;
    
      // Função auxiliar para identificar se o caractere é alfanumérico
      const ehValido = (char) => /[a-z0-9]/.test(char);
    
      while (esquerda < direita) {
        // Pula caracteres inválidos na esquerda
        if (!ehValido(str[esquerda])) {
          esquerda++;
          continue;
        }
        // Pula caracteres inválidos na direita
        if (!ehValido(str[direita])) {
          direita--;
          continue;
        }
    
        // Compara os caracteres válidos
        if (str[esquerda] !== str[direita]) {
          return false; // Break imediato: não é palíndromo
        }
    
        esquerda++;
        direita--;
      }
    
      return true;
    }
    
    // Testes
    console.log(ePalindromo("arara")); // true
    console.log(ePalindromo("A man, a plan, a canal: Panama")); // true
    console.log(ePalindromo("JavaScript")); // false
    ```
    
*   2 questão Verificar Anagrama
    
    Problema
    
    Dadas duas strings, verifique se uma é anagrama da outra.
    
    Entrada
    
    ```bash
    
    "listen"
    "silent"
    
    
    ```
    
    Saída
    
    ```bash
    
    true
    
    
    ```
    
    Regras
    
    *   Ignore espaços
    *   Ignore case
    *   Não use sort inicialmente (quero ver estrutura de dados)
    
    RESOLUÇÃO
    
    ```plain
    function saoAnagramas(str1, str2) {
      // 1. Limpeza e Normalização
      const s1 = str1.toLowerCase().replace(/\s+/g, '');
      const s2 = str2.toLowerCase().replace(/\s+/g, '');
    
      // 2. Verificação de tamanho (Early Return)
      if (s1.length !== s2.length) return false;
    
      const contagem = {};
    
      // 3. Mapeando a primeira string
      for (let letra of s1) {
        contagem[letra] = (contagem[letra] || 0) + 1;
      }
    
      // 4. Comparando com a segunda string
      for (let letra of s2) {
        // Se a letra não existe ou a contagem chegou a 0, não é anagrama
        if (!contagem[letra]) {
          return false; 
        }
        contagem[letra] -= 1;
      }
    
      return true;
    }
    
    // Testes
    console.log(saoAnagramas("listen", "silent")); // true
    console.log(saoAnagramas("Aba caxi", "Caixa ba")); // true
    console.log(saoAnagramas("rat", "car")); // false
    
    
    ```
    
    *   
*   questão 3 Contar Frequência de Caracteres
    
    🎯 Problema
    
    Dada uma string, retorne a frequência de cada caractere.
    
    Entrada
    
    ```bash
    
    "banana"
    
    
    ```
    
    Saída
    
    ```css
    
    {
      b:1,
      a:3,
      n:2
    }
    
    
    ```
    
    Perguntas depois:
    
    *   Qual a complexidade?
    *   Como lidar com Unicode?
    
    Resposta
    
    ```plain
    function createObject(word){
      let object = {}
      for( let char of word){
        object[char] = object[char] ? 
          object[char] + 1 : 1
      }
      return object
    }
    ```
    
    Muito foco aqui, pois se a resposta certa nesse caso para javascript seria usar "char of word" pq o "of" analisa emoj e letras com asento da maneira correta
    
*   questão 4 Substring Mais Longa Sem Repetição
    
    Problema
    
    Encontre o tamanho da maior substring sem caracteres repetidos.
    
    Entrada
    
    ```bash
    
    "abcabcbb"
    
    
    ```
    
    Saída
    
    ```bash
    
    3   // "abc"
    
    
    ```
    
    Outro exemplo
    
    ```bash
    
    "bbbbb"
    
    
    ```
    
    Saída:
    
    ```plain
    
    1
    
    
    ```
    
    Restrição
    
    *   O(n)
    *   Não pode usar brute force
    
    Resposta
    
    ```plain
    function lengthOfLongestSubstring(s) {
      let left = 0
      let maxLength = 0
      const seen = new Set()
    
      for (let right = 0; right < s.length; right++) {
        while (seen.has(s[right])) {
          seen.delete(s[left])
          left++
        }
    
        seen.add(s[right])
        maxLength = Math.max(maxLength, right - left + 1)
      }
    
      return maxLength
    }
    
    console.log(lengthOfLongestSubstring("abcabcdjaaaaa")) // 3
    console.log(lengthOfLongestSubstring("bbbbb"))    // 1
    ```
    
    1. 
*   Questão 5 Dado um array de strings, retorne para cada palavra o menor prefixo que a torne única no conjunto.
    
    Exemplo
    
    Entrada:
    
    ```css
    
    ["dog","racecar","car","duck","dogar"]
    
    
    ```
    
    Resposta
    
    ```css
    class TrieNode {
      constructor() {
        this.children = {}
        this.count = 0
      }
    }
    
    class Trie {
      constructor() {
        this.root = new TrieNode()
      }
    
      insert(word) {
        let node = this.root
    
        for (let char of word) {
          if (!node.children[char]) {
            node.children[char] = new TrieNode()
          }
    
          node = node.children[char]
          node.count++
        }
      }
    
      findUniquePrefix(word) {
        let node = this.root
        let prefix = ""
    
        for (let char of word) {
          node = node.children[char]
          prefix += char
    
          if (node.count === 1) {
            break
          }
        }
    
        return prefix
      }
    }
    
    function shortestUniquePrefixes(words) {
      const trie = new Trie()
    
      // Inserir todas as palavras
      for (let word of words) {
        trie.insert(word)
      }
    
      // Encontrar prefixos únicos
      const result = []
      for (let word of words) {
        result.push(trie.findUniquePrefix(word))
      }
    
      return result
    }
    
    console.log(shortestUniquePrefixes(["dog","racecar","car","duck","dogar", "zebra"]))
    ```
    
    Saída esperada:
    
## HashMap
*   1 questão Primeiro Elemento Repetido
    
    roblema
    
    Dado um array de números, retorne o **primeiro elemento que aparece duas vezes**.
    
    Entrada
    
    ```cs
    
    [2,5,1,2,3,5,1]
    
    
    ```
    
    Saída
    
    ```plain
    
    2
    
    
    ```
    
    Requisitos
    
    *   O(n)
    *   Não usar dois loops
    *   Detectar duplicado o mais rápido possível
    
    Resposta
    
    ```plain
    class Trie {  
      insertNumbers(numbers){
        let children = {}
        
        for(let number of numbers){
          if(children[number]){
            return number
          }
          children[number]=1
        }
      }
      
    }
    
    const trie = new Trie
    
    
    console.log(trie.insertNumbers([2,5,2,1,3,6,1]))
    ```
    
    ou
    
    ```plain
    function firstDuplicate(array) {
      const seen = new Set()
    
      for (let num of array) {
        if (seen.has(num)) {
          return num
        }
        seen.add(num)
      }
    
      return null
    }
    
    console.log(firstDuplicate([2,5,1,2,3,5,1])) // 2
    ```
    
*   2 questãoElementos Únicos (Single Number II)
    
    roblema
    
    Todos os números aparecem duas vezes, exceto um.
    
    Retorne o número que aparece apenas uma vez.
    
    Entrada
    
    ```cs
    
    [4,1,2,1,2]
    
    
    ```
    
    Saída
    
    ```plain
    
    4
    
    
    ```
    
    Requisitos
    
    *   O(n)
    *   Preferencialmente O(1) espaço (se souber otimizar depois)
    
    REsposta
    
    ```plain
    class Trie {  
      insertNumbers(numbers){
        let repeat = new Set()
        
        for(let number of numbers){
          if(repeat.has(number)){
            repeat.delete(number)
          }else{
            repeat.add(number)
          }
         
        }
        
        return repeat
      }
      
      
    }
    
    const trie = new Trie
    
    
    console.log(trie.insertNumbers([4,1,2,1,2]))
    
    function singleNumber(nums) {
      let result = 0
    
      for (let num of nums) {
        result ^= num
      }
    
      return result
    }
    
    console.log(singleNumber([4,1,2,1,2])) // 4
    ```
    
*   3 Questão Subarray com Soma Igual a K
    
    Subarray com Soma Igual a K
    
    🎯 Problema
    
    Dado um array e um número k, retorne `true` se existir um subarray contínuo cuja soma seja k.
    
    Entrada
    
    ```cs
    
    [1,2,3,4,5]
    k = 9
    
    
    ```
    
    Saída
    
    ```cpp
    
    true  // porque 2+3+4 = 9
    
    
    ```
    
    Foco
    
    *   Prefix sum + HashMap
    *   Transformar O(n²) em O(n)
    *   Muito comum em entrevistas
    
    ```plain
    function hasSubarraySum(nums, k) {
      const seen = new Set()
      let prefixSum = 0
    
      seen.add(0) // importante para caso soma desde o início
    
      for (let num of nums) {
        prefixSum += num
    
        if (seen.has(prefixSum - k)) {
          return true
        }
    
        seen.add(prefixSum)
      }
    
      return false
    }
    
    console.log(hasSubarraySum([1,2,3,4,5], 9)) // true
    ```
    
*   4 questão Maior Frequência
    
    Dado um array, retorne o número que aparece mais vezes.
    
    Entrada
    
    ```cs
    
    [1,3,2,3,4,3,5]
    
    
    ```
    
    Saída
    
    ```plain
    
    3
    
    
    ```
    
    Foco
    
    *   Contagem de frequência
    *   HashMap
    *   Analisar empate
    
    ```plain
    function hasSubarraySum(nums) {
     const seen = new Set()
     const frequency = {}
     let biggerNumber = 0
     let biggerFrequency = 0
     seen.add(0)
      
      for(let num of nums){
        frequency[num] ? frequency[num] = frequency[num]+1:  frequency[num] = 1 
        
        if(frequency[num] > biggerFrequency){
          biggerFrequency = frequency[num]
          biggerNumer = num
        }
        
      }
      
      return biggerNumer
    }
    
    console.log(hasSubarraySum([1,3,2,4,4,3,4,3,3,5,5,5,5,5])) // true
    ```
    
# Stack (Pilha)
*   Questão 1 — Parênteses Válidos (Clássica)
    
    Dada uma string `s` contendo apenas os caracteres:
    
    ```scss
    ( ) { } [ ]
    
    
    ```
    
    Implemente uma função que determine se a string é válida.
    
    Uma string é válida se:
    
    *   Todo símbolo de abertura tem um símbolo de fechamento correspondente.
    *   Os símbolos são fechados na ordem correta.
    *   Cada fechamento corresponde ao tipo correto.
    
    ```plain
    function isValid(s) {
      const stack = [];
      const map = { ')': '(', ']': '[', '}': '{' };
    
      for (const char of s) {
        if (char === '(' || char === '[' || char === '{') {
          stack.push(char); // Guarda a abertura
        } else {
          // Se fechar, o topo da pilha tem que ser a abertura correspondente
          if (stack.pop() !== map[char]) return false;
        }
      }
      return stack.length === 0; // Se sobrou algo, está errado
    }
    ```
    
*   2 questão — Parênteses Válidos com Curinga (\*)
    
    Agora a string pode conter:
    
    ```scss
    ( ) *
    
    
    ```
    
    O caractere `*` pode representar:
    
    *   `(`
    *   `)`
    *   ou string vazia
    
    Determine se a string pode ser válida.
    
    Exemplos
    
    ```yaml
    Input: "(*)"
    Output: true
    
    Input: "(*))"
    Output: true
    
    Input: "(((*)"
    Output: false
    ```
    
    resolução
    
    ```plain
    function checkValidString(s) {
        let minOpen = 0;
        let maxOpen = 0;
    
        for (let char of s) {
            if (char === "(") {
                minOpen++;
                maxOpen++;
            } else if (char === ")") {
                minOpen--;
                maxOpen--;
            } else { // '*'
                minOpen--;   // se for ')'
                maxOpen++;   // se for '('
            }
    
            if (maxOpen < 0) return false;
    
            if (minOpen < 0) minOpen = 0;
        }
    
        return minOpen === 0;
    }
    
    
    console.log(checkValidString("))(("))
    ```
    
*   Questão 3 — Implementar Undo / Redo
    
    Implemente uma estrutura `TextEditor` com as operações:
    
    ```erlang
    append(text)     → adiciona texto
    undo()           → desfaz última operação
    redo()           → refaz última operação desfeita
    getText()        → retorna texto atual
    
    
    ```
    
    Regras
    
    *   Você deve usar **duas pilhas**.
    *   Se o usuário fizer uma nova operação após um undo, o histórico de redo deve ser apagado.
    
    Exemplo
    
    ```erlang
    append("a")
    append("b")
    getText() → "ab"
    
    undo()
    getText() → "a"
    
    redo()
    getText() → "ab"
    ```
    
    resposta
    
    ```plain
    let history = []
    let future = []
    
    function append(string){
      history.push(string)
      future = []
      
    }
    
    function getText(){
      console.log(history.join(""))
    }
    
    function undo(){
      future.push(history.pop())
    }
    
    function redo(){
      if(future.length > 0 ){
        history.push(future.pop())
      }
      
    }
    
    
    
    
    append("a")
    append("b")
    getText()
    
    undo()
    undo()
    getText()
    redo()
    getText()
    
    
    ```
    
*   questão 4 - Avaliar Expressão Pós-Fixa (Reverse Polish Notation)
    
    Dado um array de strings representando uma expressão em **notação pós-fixa**, avalie o resultado.
    
    Operadores válidos:
    
    ```diff
    + - * /
    
    
    ```
    
    Exemplos
    
    ```css
    Input: ["2","1","+","3","*"]
    Output: 9
    Explicação: ((2 + 1) * 3)
    
    Input: ["4","13","5","/","+"]
    Output: 6
    Explicação: (4 + (13 / 5))
    
    
    ```
    
    Observações
    
    *   Divisão inteira truncada para zero.
    *   A expressão sempre será válida.
    
    resposta
    
    ```plain
    function mathNotetion(notetions){
      const stack = []
      for (notetion of notetions){
        if (!isNaN(notetion)) {
          stack.push(Number(notetion));
        } else {
          const b = stack.pop();
          const a = stack.pop();
    
          let result;
    
          if (notetion === "+") {
              result = a + b;
          } else if (notetion === "-") {
              result = a - b;
          } else if (notetion === "*") {
              result = a * b;
          } else if (notetion === "/") {
              result = Math.trunc(a / b); // truncar para zero
          }
    
          stack.push(result);
        }
      }
      return stack.pop()
    }
    
    
    console.log(mathNotetion(["2","1","+","1","*"]))
    ```
    
*   Questão 5 Questão 5 — Min Stack (Stack com mínimo em O(1))
    
    Implemente uma stack que suporte:
    
    ```scss
    push(x)
    pop()
    top()
    getMin()
    
    
    ```
    
    Todas as operações devem rodar em **O(1)**.
    
    Exemplo
    
    ```scss
    push(-2)
    push(0)
    push(-3)
    getMin() → -3
    pop()
    top() → 0
    getMin() → -2
    ```
    
    resposta
    
    ```css
    class Stack {
      constructor(){
        this.min = []
        this.stack = []
      }
      
      push(number){
        this.stack.push(number)
        if(this.min.length === 0 || number <= this.min[this.min.length - 1]){
          this.min.push(number)
        }
      }
      
      getMin(){
        console.log("minimo", this.min[this.min.length - 1])
      }
      
      pop(){
        if(this.stack.pop() === this.min[this.min.length - 1]){
          this.min.pop()
        }
      }
      
      top(){
        console.log("pegar o primeiro", this.stack[this.stack.length - 1])
      }
      
    }
    
    stack = new Stack
    
    
    stack.push(-2)
    stack.push(0)
    stack.push(-3)
    stack.getMin() // → -3
    stack.pop()
    stack.top()// → 0
    stack.getMin() //→ -2
    ```
    
## Queue (Fila)
*   Questão 1 Implementar Queue usando duas Stacks
    
    Implemente:
    
    ```erlang
    enqueue(x)
    dequeue()
    peek()
    empty()
    
    
    ```
    
    Mas você só pode usar **duas stacks**.
    
    resposta
    
    ```plain
    class MyQueue {
      constructor() {
        this.stackIn = [];  // Pilha para inserção
        this.stackOut = []; // Pilha para remoção
      }
    
      // Adicionar: Sempre O(1)
      enqueue(x) {
        this.stackIn.push(x);
      }
    
      // Remover: O(1) amortizado
      dequeue() {
        this._transfer();
        return this.stackOut.pop();
      }
    
      // Espiar o primeiro: O(1) amortizado
      peek() {
        this._transfer();
        return this.stackOut[this.stackOut.length - 1];
      }
    
      // Verificar se está vazia
      empty() {
        return this.stackIn.length === 0 && this.stackOut.length === 0;
      }
    
      // Método auxiliar para inverter as stacks
      _transfer() {
        // Só transferimos se a stack de saída estiver vazia!
        if (this.stackOut.length === 0) {
          while (this.stackIn.length > 0) {
            this.stackOut.push(this.stackIn.pop());
          }
        }
      }
    }
    
    // Teste
    const fila = new MyQueue();
    fila.enqueue(1);
    fila.enqueue(2);
    console.log(fila.peek());    // 1
    console.log(fila.dequeue()); // 1
    console.log(fila.empty());   // false
    ```
    
*   Questão 2 — Binary Tree Level Order Traversal
    
    Dada a raiz de uma árvore binária, retorne os valores nível por nível.
    
    Exemplo:
    
    ```cs
    Input:
            3
           / \
          9  20
             / \
            15  7
    
    Output:
    [
      [3],
      [9,20],
      [15,7]
    ]
    ```
    
    Resposta
    
    ```plain
    class TreeNode {
      constructor(val, left = null, right = null) {
        this.val = val;
        this.left = left;
        this.right = right;
      }
    }
    
    const root = new TreeNode(
      3,
      new TreeNode(9),
      new TreeNode(
        20,
        new TreeNode(15),
        new TreeNode(7)
      )
    );
    
    function levelOrder(root) {
     if(!root) return
      
      console.log(root)
      const result = [root.val]
      const queue = [root]
      let head = 0
      
      while(queue.length > 0){
        const levelSize = queue.length
        const currentLevel = queue.pop()
        
        if(currentLevel.left){
          queue.push(currentLevel.left)
          result.push(currentLevel.left.val)
        }
        if(currentLevel.right){
          queue.push(currentLevel.right)
          result.push(currentLevel.right.val)
        }      
        
      }
      
      
      
      
      return result
      
    }
    
    
    console.log(levelOrder(root));
    ```
    
*   Questão 3 — Número de Ilhas (BFS em Grid)
    
    Dado um grid 2D com:
    
    *   `"1"` = terra
    *   `"0"` = água
    
    Conte quantas ilhas existem.
    
    Exemplo:
    
    ```scheme
    [
     ["1","1","0","0"],
     ["1","0","0","1"],
     ["0","0","1","1"]
    ]
    ```
    
    Resposta
    
    ```plain
    function numIslands(grid) {
      if (!grid || grid.length === 0) return 0;
    
      let count = 0;
      const rows = grid.length;
      const cols = grid[0].length;
    
      const directions = [
        [1, 0],
        [-1, 0],
        [0, 1],
        [0, -1]
      ];
    
      function bfs(r, c) {
        const queue = [[r, c]];
        let head = 0;
    
        grid[r][c] = "0";
    
        while (head < queue.length) {
          const [row, col] = queue[head++];
    
          for (let [dr, dc] of directions) {
            const newRow = row + dr;
            const newCol = col + dc;
    
            if (
              newRow >= 0 &&
              newRow < rows &&
              newCol >= 0 &&
              newCol < cols &&
              grid[newRow][newCol] === "1"
            ) {
              grid[newRow][newCol] = "0";
              queue.push([newRow, newCol]);
            }
          }
        }
      }
    
      for (let r = 0; r < rows; r++) {
        for (let c = 0; c < cols; c++) {
          if (grid[r][c] === "1") {
            count++;
            bfs(r, c);
          }
        }
      }
    
      return count;
    }
    
    
    // Teste com o exemplo
    const mapa = [
     ["1","0"],
     ["1","1"],
    ];
    
    console.log(numIslands(mapa)); // Saída: 3
    ```
    
*   Questão 4 — Rotting Oranges (Clássica Amazon)
    
    Grid com: 0 = vazio 1 = laranja fresca 2 = laranja podre A cada minuto, laranjas podres contaminam as adjacentes. Retorne quantos minutos até todas ficarem podres. Se impossível, retorne -1.
    
    Resposta
    
    ```plain
    function orangesRotting(grid) {
      const rows = grid.length;
      const cols = grid[0].length;
    
      const queue = [];
      let head = 0;
      let fresh = 0;
      let minutes = 0;
    
      // 1️⃣ Inicialização
      for (let r = 0; r < rows; r++) {
        for (let c = 0; c < cols; c++) {
          if (grid[r][c] === 2) {
            queue.push([r, c]); // multi-source
          }
          if (grid[r][c] === 1) {
            fresh++;
          }
        }
      }
    
      // Se não tem laranja fresca
      if (fresh === 0) return 0;
    
      const directions = [
        [1,0],
        [-1,0],
        [0,1],
        [0,-1]
      ];
    
      // 2️⃣ BFS por nível
      while (head < queue.length) {
        const size = queue.length - head;
        let infectedThisRound = false;
    
        for (let i = 0; i < size; i++) {
          const [r, c] = queue[head++];
    
          for (let [dr, dc] of directions) {
            const nr = r + dr;
            const nc = c + dc;
    
            if (
              nr >= 0 &&
              nr < rows &&
              nc >= 0 &&
              nc < cols &&
              grid[nr][nc] === 1
            ) {
              grid[nr][nc] = 2;
              queue.push([nr, nc]);
              fresh--;
              infectedThisRound = true;
            }
          }
        }
    
        if (infectedThisRound) minutes++;
      }
    
      return fresh === 0 ? minutes : -1;
    }
    ```
    
*   Questão 5 — Shortest Path em Grafo Não Ponderado
    
    Dado um grafo e dois nós `start` e `end`, encontre a menor distância.
    
    ⚠️ Dica: Em grafo não ponderado, menor caminho = BFS.
    
    📌 Resumo mental importante
    
    Estrutura Usa o quê
    
    DFS Stack
    
    BFS Queue
    
    Menor caminho sem peso BFS
    
    Processar por nível BFS
    
    REsposta
    
    ```cpp
    const graph = {
      A: ["B", "D"],
      B: ["A", "C"],
      C: ["B", "E"],
      D: ["A", "E"],
      E: ["D", "C"]
    };
    
    
    
    function fastWay(graph, start, end){
      if(start === end) return 0
      
      let distance = 0
      let head =0
      const conectionList = new Set()
      const queue =[{node: start, distance: 0}]
      conectionList.add(start)
      
        while(head < queue.length){
          const { node, distance } = queue[head]
          head = head+1
        
          for(conection of graph[node]){
            if(conection === end) return distance +1
            if(!conectionList.has(conection)){
              conectionList.add(conection)
              queue.push({ node: conection, distance: distance + 1 });  
            }
          }
        }
        
        
      
      
      
      
      return distance
    }
    
    
    console.log(fastWay(graph,"A", "E"))
    ```
    
## Dois Ponteiros
*   Questão 1 — Two Sum II (Array Ordenado)
    
    Dado um array **ordenado crescente** e um `target`, encontre dois números cuja soma seja igual ao target.
    
    Retorne os índices (1-based).
    
    Exemplo
    
    ```yaml
    Input: numbers = [2,7,11,15], target = 9
    Output: [1,2]
    
    
    ```
    
    Restrições
    
    *   O array já está ordenado.
    *   Deve rodar em O(n).
    *   Não pode usar HashMap.
    
    Resposta PARA alinhado
    
    ```plain
    const numbers = [2,7,11,15]
    const target = 9
    
    console.log(findIndexs(numbers, target))
    
    function findIndexs(numbers, target){
      let leftIndex = 0
      let rightIndex = numbers.length -1
      
      while(leftIndex < rightIndex){
        if((numbers[leftIndex]+numbers[rightIndex]) === target) {
          return [leftIndex+1, rightIndex+1]
        }
        (numbers[leftIndex]+numbers[rightIndex]) < target ?
          leftIndex = leftIndex +1 :
          rightIndex =rightIndex -1
      }  
    }
    ```
    
    reposta para desorganizado
    
    ```plain
    const numbers = [2,7,11,15]
    const target = 9
    
    console.log(findIndexs(numbers, target))
    
    function findIndexs(numbers, target){
      const seen = {}
      
      for(let i = 0; i < numbers.length; i++){
        if(seen[target - numbers[i]]){
           return [seen[target -numbers[i]], i+1]
        }
        seen[numbers[i]]= i+1
      }
      
      
    }
    ```
    
*   Questão 2 — Verificar Palíndromo (Ignorando caracteres não alfanuméricos)
    
    Dada uma string, determine se ela é um palíndromo considerando apenas letras e números.
    
    Ignore maiúsculas/minúsculas.
    
    Exemplo
    
    ```yaml
    Input: "A man, a plan, a canal: Panama"
    Output: true
    
    
    Input: "race a car"
    Output: false
    ```
    
    Resposta
    
    ```plain
    const word = "abba"
    const word2 = "abab"
    const word3 = "A man, a plan, a canal: Panama"
    
    console.log(isPalindromo(word3))
    
    function isPalindromo(word){
      const seen = {}
      const cleanStr = word.toLowerCase().replace(/[^a-z0-9]/g, "");
      let left = 0
      let rigth = cleanStr.length -1
      
      while(left<rigth){
        if(!(cleanStr[left] === cleanStr[rigth])){
          return false
        }
        left++
        rigth--
      }  
      
      return true
    }
    ```
    
*   Questão 3 — Remover Duplicados de Array Ordenado (In-place)
    
    Dado um array ordenado, remova duplicados **sem usar array extra**.
    
    Retorne o novo tamanho.
    
    Exemplo
    
    ```yaml
    Input: [1,1,2]
    Output: 2
    Array modificado: [1,2,_]
    
    
    Input: [0,0,1,1,1,2,2,3,3,4]
    Output: 5
    Array: [0,1,2,3,4,_,_,_,_,_]
    ```
    
    Resposta
    
    ```php
    const array = [0,0,1,1,1,2,2,3,3,4,4,5]
    
    console.log(removeRepeat(array))
    
    function removeRepeat(array){
      const seen = {}
      let left = 0
      let rigth = 1
      let length = array.length
      
      while(left < array.length-1){
        if((array[left] === array[rigth])){
          length--
        }
        left = rigth
        rigth++
      }  
      
      return length
    }
    ```
    
*   Questão 4 — 3Sum (Clássica Difícil)
    
    Dado um array de inteiros, encontre todos os triplets únicos que somam 0.
    
    Exemplo
    
    ```yaml
    Input: [-1,0,1,2,-1,-4]
    
    Output:
    [
     [-1,-1,2],
     [-1,0,1]
    ]
    
    
    ```
    
    Regras
    
    *   Não pode ter triplets duplicados.
    *   Complexidade ideal: O(n²)
    
    Resposta
    
    ```plain
    function threeSum(nums) {
      nums.sort((a, b) => a - b);
      const result = [];
    
      for (let i = 0; i < nums.length - 2; i++) {
        
        // Evitar duplicado no primeiro número
        if (i > 0 && nums[i] === nums[i - 1]) continue;
    
        let left = i + 1;
        let right = nums.length - 1;
    
        while (left < right) {
          const sum = nums[i] + nums[left] + nums[right];
    
          if (sum === 0) {
            result.push([nums[i], nums[left], nums[right]]);
    
            // Pular duplicados
            while (left < right && nums[left] === nums[left + 1]) left++;
            while (left < right && nums[right] === nums[right - 1]) right--;
    
            left++;
            right--;
          } 
          else if (sum < 0) {
            left++;
          } 
          else {
            right--;
          }
        }
      }
    
      return result;
    }
    const nums = [-1,0,1,2,-1,-4]
    console.log(threeSum(nums))
    ```
    
*   Questão 5 — Container With Most Water
    
    Dado um array `height[]`, cada elemento representa a altura de uma linha vertical.
    
    Encontre duas linhas que juntas formam o container com maior área.
    
    Exemplo
    
    ```yaml
    Input: [1,8,6,2,5,4,8,3,7]
    Output: 49
    
    
    ```
    
    Área = largura × menor altura
    
    ```plain
    function maxArea(height) {
      let maxA = 0;
      let left = 0;
      let right = height.length - 1;
    
      while (left < right) {
        // 1. Calcular a largura entre as colunas
        let largura = right - left;
        
        // 2. A altura útil é sempre a da menor coluna (o balde não transborda)
        let alturaUtil = Math.min(height[left], height[right]);
        
        // 3. Atualizar o recorde de área
        let areaAtual = largura * alturaUtil;
        maxA = Math.max(maxA, areaAtual);
    
        // 4. Estratégia: Mover quem está "atrapalhando" a altura
        if (height[left] < height[right]) {
          left++;
        } else {
          right--;
        }
      }
    
      return maxA;
    }
    
    // Teste
    const h = [1, 8, 6, 2, 5, 4, 8, 3, 7];
    console.log(maxArea(h)); // Saída: 49 (entre o 8 no índice 1 e o 7 no índice 8)
    ```
    
# Busca Binária
*   Busca Binária
    
    Dado um array ordenado crescente `nums` e um `target`, retorne o índice do elemento.
    
    Se não existir, retorne `-1`.
    
    Exemplo
    
    ```yaml
    Input: nums = [-1,0,3,5,9,12], target = 9
    Output: 4
    
    
    Input: nums = [-1,0,3,5,9,12], target = 2
    Output: -1
    ```
    
    resposta
    
    ```plain
    function binarySearch(nums, target) {
      let inicio = 0;
      let fim = nums.length - 1;
    
      while (inicio <= fim) {
        // Math.floor para garantir um número inteiro no índice
        // Dica de performance: let meio = Math.floor(inicio + (fim - inicio) / 2);
        let meio = Math.floor((inicio + fim) / 2);
    
        if (nums[meio] === target) {
          return meio; // Encontrou!
        }
    
        if (nums[meio] < target) {
          inicio = meio + 1; // O target está na metade da direita
        } else {
          fim = meio - 1;    // O target está na metade da esquerda
        }
      }
    
      return -1; // Não existe no array
    }
    
    // Teste
    console.log(binarySearch([-1, 0, 3, 5, 9, 12], 9)); // 4
    console.log(binarySearch([-1, 0, 3, 5, 9, 12], 2)); // -1
    ```
    
*   Questão 2 — Search Insert Position
    
    Dado um array ordenado e um `target`, retorne o índice onde ele está
    
    ou onde deveria ser inserido para manter a ordem.
    
    Exemplo
    
    ```yaml
    Input: nums = [1,3,5,6], target = 5
    Output: 2
    
    
    Input: nums = [1,3,5,6], target = 2
    Output: 1
    
    
    Input: nums = [1,3,5,6], target = 7
    Output: 4
    ```
    
    resposta
    
    ```javascript
    function searchInsert(nums, target) {
      let inicio = 0;
      let fim = nums.length - 1;
    
      while (inicio <= fim) {
        // Usamos o truque matemático para pegar o inteiro do meio
        let meio = Math.floor((inicio + fim) / 2);
    
        if (nums[meio] === target) {
          return meio; // Caso fácil: o número já existe
        }
    
        if (nums[meio] < target) {
          inicio = meio + 1; // O target é maior, busca na direita
        } else {
          fim = meio - 1;    // O target é menor, busca na esquerda
        }
      }
    
      // Se o loop acabar e não retornou 'meio', 
      // o 'inicio' será o índice de inserção.
      return inicio;
    }
    
    // Testes
    console.log(searchInsert([1, 3, 5, 6], 5)); // 2
    console.log(searchInsert([1, 3, 5, 6], 2)); // 1
    console.log(searchInsert([1, 3, 5, 6], 7)); // 4
    console.log(searchInsert([1, 3, 5, 6], 0)); // 0
    ```
    
*   Questão 3 — Encontrar Pico (Find Peak Element)
    
    Um pico é um elemento maior que seus vizinhos.
    
    Retorne qualquer índice de pico.
    
    Exemplo
    
    ```yaml
    Input: [1,2,3,1]
    Output: 2
    
    
    Input: [1,2,1,3,5,6,4]
    Output: 1 ou 5
    
    
    ```
    
    ⚠️ Deve rodar em O(log n)
    
    ```plain
    function findPeakElement(nums) {
      let inicio = 0;
      let fim = nums.length - 1;
    
      while (inicio < fim) {
        let meio = Math.floor((inicio + fim) / 2);
    
        // Comparamos o meio com o seu vizinho da direita
        if (nums[meio] < nums[meio + 1]) {
          // Estamos em uma subida! 
          // O pico com certeza está à direita (e o meio + 1 pode ser o pico)
          inicio = meio + 1;
        } else {
          // Estamos em uma descida!
          // O pico está à esquerda ou é o próprio elemento do meio
          fim = meio;
        }
      }
    
      // No final, inicio e fim se encontram no ponto mais alto (o pico)
      return inicio;
    }
    
    // Testes
    console.log(findPeakElement([1, 2, 3, 1]));       // Saída: 2 (valor 3)
    console.log(findPeakElement([1, 2, 1, 3, 5, 6, 4])); // Saída: 5 (valor 6)
    ```