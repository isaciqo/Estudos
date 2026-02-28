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
    

*     
    

  

*