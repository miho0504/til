udemy TypeScriptとVueコンポーネント！！！

jsフレームワーク
vueはリアクティブ（反応が早いものを作る際にいい）

______________________________________________________________________

※const を使って変数を宣言する場合、宣言時に必ず初期値を指定する必要があります。
そしてあとから別の値を代入することができません。

🌟ref関数インポートの必要
import { ref } from 'vue'

🌟ref関数はitemName1の値が変わったらそれに伴って変わる。deskは初期値

const itemName1 = ref<string>('Desk')

const input = (event: any) => {
  itemName1.value = event.target.value
}

inputで入力された値はvalueとなっている


🌟コンポーネント再利用可能（部品と考える）
importで読み込みコンポーネント

<template>html記載</template>
<style scoped>css記載</style>
ディレクティブを使って動的なものを作る

<a v-bind:href="url11">mihho</a>
const url1 = "URL"

////////

🐳①Are you sure to buy desk  ?'アラート出力したい

const itemName1 = 'Desk'
const buy = () => {
  alert('Are you sure to buy + itemName1 + ?')
}
// デスクのBUYボタンを押した際の処理
<button v-on:click="buy(itemName1)">BUY</button>

→Are you sure to buy desk  ?'出力



🐳②入力箇所に入力したらメニュー名が変わって欲しい

// letで新しく値を代入することができる
let itemName1 = 'Desk'

// eventの引数を受け取りその中のtarget.valueとして受け取り
// itemName1に新しい文字列として入れている

const input = (event: any) => {
  console.log('event.target.value:',event.target.value: )
  itemName1 = event.target.value
}
<input v-on:input="input" />

でもこれじゃ変わらないスクリプトないで定義しているものが変わったとしてもテンプレートには反映されない

🌟何をすればいいか
変数が変わったらvueに再度テンプレートを読み込めと指示する、りアクティブな値を使う

// リアクティブな状態の宣言
import {ref} from 'vue'

// 初期値がdesk string型
内部の値を受け取り、リアクティブでミュータブルな ref オブジェクトを返します。

const itemName1 = ref<string>('Desk')

// eventの引数を受け取りその中のtarget.valueとして受け取り
// itemName1に新しい文字列として入れている

const input = (event: any) => {
  console.log('event.target.value:',event.target.value: )

  🌟refに対しては.valueをつけてあげる（オブジェクトのプロパティに関しては再度値えれる）
  itemName1.value = event.target.value
}
<input v-on:input="input" />

→これでitemName1の値が変わるとテンプレートが再度読み込まれる


🌟refの他にreactiveがある
例えばみたいにそれぞれ定義されている場合(複数にしたい場合)

const itemName1 = ref<string>('Desk')
const price1 = 10000

import {ref, reactive} from 'vue'

// オブジェクト形式で表現
const item1 = reactive({
  name: 'Desk',
  price: 10000
})

const input = (event: any) => {
  console.log('event.target.value:',event.target.value: )
  item1.name = event.target.value
}

const input = (event: any) => {
  console.log('event.target.value:',event.target.value: )
  item1.price = event.target.value
}

<label>({item1.name})</label>
<label>({item1.price})yen</label>

<input v-on:input="input" />
<input v-on:input="inputPrice" />

③🌟クリアボタン
<button v-on:click="Clear">Crear</button>

// 以下のオブジェクト定義
const Clear = () => {
  item1.name = ''
  item1.price = 0
}

// これでクリア押すとinput内がクリアされる
<input v-on:input="input" v-bind:value="item1.name" />
<input v-on:input="inputPrice" v-bind:value="item1.price"/>

🔥簡略化（こちらが一般的）
<input v-model="item1.name" />

input 要素に v-model という属性をつけることで、インスタンス上のデータと input 要素の入力値を同期することができます。これを双方向データバインディングと呼びます。


④もし5マンより大きかったらtoo expencive表示の三項演算子
import {ref, reactive, computed} from 'vue'
const budget = 50000

const priceLabel = computed(() => {
  if (item1.price > budget) {
    return 'too expencive'
  } else if (item1.price > budget) {
    return 'too0000 expencive'
  } else {
    return item1.price + 'yen'
  }
})

<label>({ priceLabel })</label>


