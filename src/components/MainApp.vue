<template>
  <div id="main">
    <div class="contact">
      <div class="container">
        <ul class="item">
          <li class="github">
            <a href="//github.com/littlegolden/syntax-highlight-word">github</a>
          </li>
          <li class="mail">
            <a
              href="//github.com/littlegolden/syntax-highlight-word/discussions"
              >mail</a
            >
          </li>
        </ul>
      </div>
    </div>
    <main>
      <div class="container">
        <h1>Syntax Highlight Code In Word Documents</h1>
        <div class="about">
          <p>
            This is a fork project to bring back the unavailable one on
            <a href="http://www.planetb.ca/syntax-highlight-word">planetb.ca</a> by Jamie.
          </p>
          <p>
            Placed a form around
            <a href="http://code.google.com/p/syntaxhighlighter/"
              >Google's SyntaxHighlighter javascript code.</a
            >
            Made it easier to use.
          </p>
          <p>
            To get some nice syntax highlighted code into a Word document, use
            IE and copy and paste some code into the form below and click the
            button. A new window will popup with the syntax highlighted code.
            Copy all and paste into your document. Unfortunately Firefox doesn't
            copy and paste into Word like IE does, so you're stuck with IE if
            you're looking to copy the resulting formatted code into a Word doc.
          </p>
        </div>
        <form-app v-on:submit="onSubmit"></form-app>
        <Highlight :data="data" :key="key"></Highlight>
      </div>
    </main>
    <footer>
      <div class="container">
        <p>
          <span id="busuanzi_container_site_pv">
            <span id="busuanzi_value_site_pv"></span> views
          </span>
        </p>
        <p>Page original designed by <a href="http://www.planetb.ca">Jamie</a></p>
      </div>
    </footer>
  </div>
</template>

<script>
import FormApp from '@/components/FormApp.vue'
import Highlight from '@/components/Highlight'
export default {
  name: 'MainApp',
  data () {
    return {
      data: {
        code: '',
        lang: ''
      },
      key: 1
    }
  },
  components: {
    FormApp,
    Highlight
  },
  methods: {
    onSubmit (e) {
      // console.log('[ e ] >', e)
      this.data = {
        code: e.code,
        lang: e.lang
      }
      // console.log('[ this ] >', this)
      ++this.key
    }
  }
}
</script>

<style lang="less">
#header {
  header {
    height: 50px;
    border-top: 5px solid #ff7e71;
    background: #373737 url(../../static/headerbackground.jpg) no-repeat center
      bottom;
    background-size: cover;
    color: #eee;
    font-weight: bold;
    font-size: 50px;
    position: relative;
    z-index: 999;
    .logo {
      height: calc(45px + 3px);
      line-height: calc(45px + 3px);
      &:after{
        content: url('../assets/new.gif')
      }
    }
  }
  nav {
    background-color: #fff;
    box-shadow: 1px 1px 2px #33333333;
    .container {
      display: flex;
    }
    .top {
      font-size: 1.2rem;
      background-color: #ff7e71;
    }
    a {
      height: 50px;
      line-height: 50px;
      display: inline-block;
    }
    a:first-child {
      width: 70px;
      text-align: center;
      color: #fff;
      margin-right: 2rem;
    }
    a:not(:first-child) {
      color: #999;
      font-size: 12px;
      letter-spacing: 1pt;
      text-align: center;
      text-decoration: none;
      padding: 0 5rem;
      text-transform: uppercase;
      &:hover {
        background-color: #ff7e71;
        color: #fff;
        text-shadow: 0px 1px 0px #9b100080;
      }
    }
  }
}
.contact {
  height: 40px;
  border-bottom: 1px solid #ccc;
  ul.item {
    width: fit-content;
    padding: 0;
    margin: 0;
    display: flex;
    list-style: none;
    margin-left: auto;
    margin-right: 0;
    > li {
      height: 40px;
      width: 40px;
      &:not(:last-child) {
        margin-right: 0.2rem;
      }
      > a {
        display: block;
        opacity: 0;
        height: 40px;
        width: 40px;
      }
    }
    > li {
      display: inline-block;
      margin: 0;
      padding: 0;
      background-image: url(../../static/socialsprites.png);
      background-repeat: no-repeat;
      transition: all 0.3s ease;
    }
    > li.github {
      background-position: 0 -1920px;
      &:hover {
        background-position: 0 -1960px;
      }
    }
    > li.mail {
      background-position: 0 -2160px;
      &:hover {
        background-position: 0 -2200px;
      }
    }
  }
}
main {
  h1 {
    margin: 0;
    padding: 20px 0 40px;
    font-weight: 300;
    font-size: 70px;
    line-height: 60px;
    color: rgba(0, 0, 0, 0.6);
    text-shadow: 0 1px 0 #fff;
    text-align: center;
    text-transform: capitalize;
  }
  .about {
    // max-width: 780px;
    max-width: 970px;
    margin-left: auto;
    margin-right: auto;
    p {
      margin-top: 0;
      margin-bottom: 20px;
      color: rgb(102, 102, 102);
      line-height: 30px;
      letter-spacing: 1pt;
      font-size: 14px;
    }
  }
}
#form {
  padding-top: 1rem;
  form {
    max-width: 970px;
    margin-left: auto;
    margin-right: auto;
    textarea {
      width: 100%;
      resize: none;
      white-space: nowrap;
    }
    .actions {
      p {
      margin-top: 0;
      margin-bottom: 20px;
      color: rgb(102, 102, 102);
      line-height: 30px;
      letter-spacing: 1pt;
      font-size: 14px;
    }
      .select {
        display: inline-block;
        margin-right: 4rem;
      }
    }
  }
}
#result {
  letter-spacing: normal;
  padding-top: 1rem;

  &.container {

    // font-size: 12px;
    &:not(.selectGunt) td.gutter,
    .toolbar {
      user-select: none;
    }
  }

  p {
      margin-top: 0;
      margin-bottom: 20px;
      color: rgb(102, 102, 102);
      line-height: 30px;
      letter-spacing: 1pt;
      font-size: 14px;
    }

  .options {
    max-width: 970px;
    margin-left: auto;
    margin-right: auto;
    user-select: none;
    color: #666;
  }

  .syntaxhighlighter .code .line.alt1 {
    background-color: #f8f8f8;
  }

  .syntaxhighlighter .gutter .line {
    border-right: none;
  }

  .code {
    letter-spacing: initial;

    .line {
      border-left: 3px solid #6ce26c;
      line-height: 14px;
    }
  }

  ol {
    margin: 0;
  }
}
footer {
  padding-top: 6rem;
  padding-bottom: 2rem;
  text-align: center;
  color: #666666;
}
</style>
