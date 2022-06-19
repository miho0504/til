udemy TypeScriptとVue

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


🌟クリアボタン
<button v-on:click="Clear">Crear</button>

const Clear = () => {
  item1.name = ''
  item1.price = 0
}




