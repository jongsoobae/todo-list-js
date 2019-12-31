<template>
  <div id="app">
    <v-container fluid>
      <v-row>
        <v-col></v-col>
        <v-col cols="6">
          <TodoInput v-on:create-memo="createMemo" />
        </v-col>
        <v-col></v-col>
      </v-row>
      <v-row class="markdown-area">
        <TodoItem v-for="(todo, index) in todoList" v-bind:key="index" :memo="todo"></TodoItem>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import TodoInput from '@/components/TodoInput'
import TodoItem from '@/components/TodoItem'
import Memo from '@/types'

export default {
  name: 'app',
  data () {
    return {
      source: '',
      id: 1,
      todoList: []
    }
  },
  components: {
    TodoInput,
    TodoItem
  },
  methods: {
    'createMemo': function (title, content) {
      let memo = new Memo(this.id++, title, content)
      memo.created = true
      this.todoList.push(memo)
    }
  }
}
</script>

<style>
.markdown-area {
  font-family: -apple-system, BlinkMacSystemFont, Segoe UI, Helvetica, Arial,
    sans-serif, Apple Color Emoji, Segoe UI Emoji;
  font-size: 16px;
  line-height: 1.5;
  word-wrap: break-word;
}

.markdown-area pre {
  display: inline-block;
  white-space: pre;
  padding: 16px;
  overflow: auto;
  font-size: 85%;
  line-height: 1.45;
  background-color: #e6e8ea;
  color: #2b2927;
  border-radius: 3px;
  word-wrap: normal;
}

.markdown-area pre code {
  display: inline-block;
  padding: 0;
  margin: 0;
  overflow: visible;
  line-height: inherit;
  word-wrap: normal;
  background-color: initial;
  border: 0 !important;

  font-size: 100%;
  word-break: normal;
  white-space: pre;
  background: transparent;
  border-radius: 3px;
  box-shadow: none;
  color: inherit;
  font-weight: 500;
}

.markdown-area pre code:after,
.markdown-area pre code:before {
  content: none !important;
}
</style>
