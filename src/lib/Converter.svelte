<script lang="ts">
 
  const convert = (keys: string, values: string) => {
    var reverse = new Map<string, string>()
    var full = new Map<string, string>()

    for (var i = keys.length; i--; ) {
      // just in case EN
      // full[keys[i].toUpperCase()] = values[i].toUpperCase()
      full[keys[i]] = values[i]
    }

    for (var a in full) {
      reverse[full[i]] = a
    }

    return {
      fromEn: function (str: string) {
        return str.replace(/./g, function (ch) {
          return full[ch] || ch
        })
      },
      toEn: function (str: string) {
        return str.replace(/./g, function (ch) {
          return reverse[ch] || ch
        })
      }
    }
  }

  const EN_TH = convert(
    "1234567890-=!@#$%^&*()_+qwertyuiop[]\\QWERTYUIOP{}|asdfghjkl;'ASDFGHJKL:\"zxcvbnm,./ZXCVBNM<>?",
    "ๅ/_ภถุึคตจขช+๑๒๓๔ู฿๕๖๗๘๙ๆไำพะัีรนยบลฃ๐\"ฎฑธํ๊ณฯญฐ,ฅฟหกดเ้่าสวงฤฆฏโฌ็๋ษศซ.ผปแอิืทมใฝ()ฉฮฺ์?ฒฬฦ"
  )

  let result: string = ""

  const conv = () => {
    const input = document.getElementById('text') as HTMLInputElement
    console.log(input.value)
    result = selectedFunc(input?.value ?? "")
  }

  let selectedFunc = EN_TH.fromEn 

  const toEn = () => {
    selectedFunc = EN_TH.toEn
    conv()
  }

  const fromEn = () => {
    selectedFunc = EN_TH.fromEn
    conv()
  }
</script>

<input type="text" id="text" on:change={conv} />
<br/>
<button on:click={toEn}>
  English
</button>
<button on:click={fromEn}>
  ไทย
</button>

<br/>
<br/>
Result in {selectedFunc === EN_TH.toEn ? 'English':'ไทย'}
<br/>
<hr/>
<br/>
<p class="result">{result}</p>

<style>
  #text {
    padding: 8px;
    font-size: 18px;
    width: auto;
    margin: auto;
  }
  .result {
    border-radius: 5%;
    padding: 2em;
  }
</style>