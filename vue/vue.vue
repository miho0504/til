🌟部品化コンポーネント
<div id="app1">
    <ul>
        <template1></template1>
    </ul>
</div>

<script>
    const App = {}

    const app = Vue.createApp(App1)

    app.component('template1', {
        template: `
            <button>ボタン</button>
        `
    })

// 呼び出し
    app.mount('#app1')
</script>

→テンプレートと書いたところにボタンが呼び出される



🌟prps
<div id="app1">
    <ul>
       <template1 prop1="次へ"></template1>
       <template1 prop1="前へ"></template1>
       <!-- 動的に -->
       <template1 prop1="varstring"></template1>
    </ul>
</div>

<script>
    const App = {
        data() {
            return {
                varstring: "hello!!"
            }
        },
    }

    const app = Vue.createApp(App1)

    app.component('template1', {
        props: ['prop1'],
        template: `
            <button>{{prop1}}</button>
        `
    })

// 呼び出し
    app.mount('#app1')
</script>

→テンプレートと書いたところにボタンが呼び出される

