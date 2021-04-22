---
title: "<4> Word Auto Compelete (tree를 활용하기)"
excerpt: "tree 와 obj의 콤비"

categories:
  - Algorithms Practice
tags:
  - 자동완성
  -
last_modified_at: 2020-08-27T09:06:00-05:00

toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---

> 1. 나름대로 개념 정리.
> 2. 각 개념에 따른 코드 정리.

# 1. Word Auto Compelete

이번에는 단어들을 저장하는 기능, 불러오는 기능, 있는지 확인하는 기능, 그리고 자동완성 기능까지 구현해보려고 한다.

Tree의 형태로 단어들을 저장할거다. 근데 이 방법은 내가 하나하나 다 구현한건 아니고 이미 있던 것을 보고 내가 이해해서 스스로 연습해보고 정리한것이다. 그럼 먼저 단어를 저장해보자.

# 1-1 단어 저장(addWord)

단어를 pass하면 글자 하나하나가 트리의 노드가 되는 형태이다. 우선 pseudo code부터 살펴보자.

- logic

- base case

  - if index equals to word.length, this.isWord is true.

- different input
  - build tree with first char of the word inside this.character
  - if the first char of the word or any sub char is inside this.characters, it uses already-existed obj
  - build tree with second char of the word inside `this.character[firstChar]`
  - keep going until` word.length === index`
  - so the deepest object is empty this.character with `this.isword = true`

재귀로 구현할거다. 단어를 이루는 글자하나하나를 dfs의 형태로 tree를 만들어나갈 생각이다. index를 올려가면서 글자를 추가한다. 만들어가다가 똑같은 글자가 있으면 그 가지를 선택해서 같이 저장한다.

그렇게 마지막 글자까지 가지를 형성한 뒤에 빈가지와 `this.isWord = true`를 만들어낸다.

```javascript
class Trie {
  constructor() {
    this.characters = {};
    this.isWord = false;
  }

  addWord(word, index = 0) {
    if (index === word.length) {
      this.isWord = true;
    } else if (index < word.length) {
      var char = word[index];
      var subTrie = this.characters[char] || new Trie();
      subTrie.addWord(word, index + 1);
      this.characters[char] = subTrie;
    }
    return this;
  }
}

var tree = new Trie();
tree.addWord("finish");
tree.addWord("cool");
tree.addWord("sexy");
tree.addWord("file");
tree.addWord("awsome");
```

그럼 아래와 같이 트리가 형성된다.

![autoAdd](https://yeonghunko.github.io/assets/img/algorithms/autoAdd.png){:class="img-fluid"}

그럼 저장된 단어 모두를 불러오는 메소드를 만들어보자.

# 1-2. 단어 불러오기(getWords)

- logic

  - loop through what's inside this.characters
  - then as you loop through you build up the character inside this.characters from empty string
  - when you reached to the end of string, which means this.isWord is true, put the accumulated string into the words array
  - return the words

array(words)를 만들어준다. 그리고 `this.characters` obj를 순회한다. key를 currentWord(빈 글자)와 합치고 그 안의 가지로 들어가서 미리 쌓아놓은 word와 다시 합친다.

그렇게 글자를 만들어가고 마지막에 `this.isWord = true`이면 그 글자를 words에다가 push한다. 이렇게 obj안에 있는 모든 key를 방문하면서 글자를 words에 저장한다.

```javascript

getWords(words = [], currentWord = '') {
  if (this.isWord) {
    words.push(currentWord);
  }
  for (var char in this.characters) {
    // currentWord 에서 계속 더해나가는 방식.
    // 그리고 words는 array이므로 마찬가지로 reference를 참조하니까 계속 built 해 나갈 수 있음
    var nextWord = currentWord + char;

     // 아하! this.characters[char] 에 할당된 value가 Trie class이므로 value안에서 method를 사용할 수 있겠구나
    this.characters[char].getWords(words, nextWord);
  }
  return words;
}

tree.getWords()
// ["finish", "file", "cool", "sexy", "awsome"]
```

그럼 결과가 위와 같이 뜬다. 참고로 `character[char]`안에 저장되어있는 것은 또다른 Trie class이므로 안에 메소드를 사용할 수 있다. 그래서 재귀 함수처럼 사용가능한것이다.

그럼 마지막으로 자동완성을 구현해보자.

# 1-3. 자동완성(AutoComplete)

- logic
  - make empty arrays for storing results
  - loop inside prefix words and trickle down inside this.characters according to letter of prefix
  - as you go down, if each of letter deosn't match any keys inside obj, then break
  - as you go down, if there is key that matches each of letter, then sink down until you hit the last letter of prefix
    - so now, the trie is the obj of last letter of prefix.
    - from there , you build up the words with prefix by pushing the array and prefix into THE trie.getwords method.
    - then return the array

그렇다. prefix로 필요한 tree를 뽑아낸다. 만약 prefix중에 하나의 단어라도 tree안에 없으면 break하고 빈 array를 리턴한다.

그렇게 필요한 tree를 뽑아내면 즉시 getWords 메소드에 tree와 array를 pass한다. 그럼 완성된 array를 뱉어내겠지?

그럼 그 완성된 array안에 prefix + 나머지 글자가 조합되어진 단어가 저장되어있다.

끝!

```javascript

  autoComplete(prefix) {
    const words = [];

    let trie = this;

    for (let char of prefix) {
      trie = trie.characters[char];
      // 예외상황
      // 예를 들어 prefix가 'fie' 라고 했을때, trie안에서 'fie' 를 가지고 계속 찾아들어간다.
      // this.characters[f]//true -> this.characters[i]//true -> this.characters[e]//undefined
      // trie = undefined가 되면 아래 코드가 실행되면서 그 즉시 for 문을 빠져 나온다
      if (!trie) {
        break;
      }
    }

    // trie가 없으므로 실행되지 않음.
    // 그럼 words = [] 가 리턴됨
    if (trie) {
      trie.getWords(words, prefix);
    }

    return words;
  }
}

tree.autoComplete('fi')
// ["finish", "file"]
```

코드가 길지는 않지만 처음엔 이해하는게 힘들었다. 단어 통째로 저장되는줄 알았는데 그게 아니고 글자 하나씩 저장되기 때문이었다. 그치만 이 코드는 가히 예술이라고 할 수 있다. 진짜 세련되고 읽기 쉽다.
