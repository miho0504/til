🌟静的なリスト

v-forディレクティブを使用することによって描画を繰り返すループ処理

const tweets = [{ id: '0', description: 'Hello, world!'}, { id: '0', description: 'this is the second tweet!'}]

<li v-for="tweet in tweets" :key="tweet.id" class="tweet-list">
    <span>{{ tweet.description }}<span>
</li>

→Hello, world
→this is the second tweet!

🌟動的なリスト（リアクティブの値を使う)

import { ref } from 'vue'

// refでリアクティブな値に
const tweets = ref([{ id: 0, description: 'Hello, world!'}, { id: 0, description: 'this is the second tweet!'}])

const inputingDescription = ref,<string>()

const postTweet = () => {
    const tweet = { id: Math.random(), description.inputingDescription.value }
    tweet.value.push(tweet)
}

// 双方向バインディング
<input v-model="inputingDescription" />
<button claas="save-button" @click="posttweet()">post</button>

🔥posttweetを押すとtweetというリアクティブな配列に対してpushというメソッドで
tweetという新しいオブジェクトを挿入できる