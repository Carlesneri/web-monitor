<script>
  import CustomBtn from '../components/atoms/button.svelte'
  import axios from 'axios'

  $:url = ''
  let resolved = ''

  const googleLogin = () => {
    console.log('google login')
  }
  const githubLogin = () => {
    console.log('github login')
  }
  const handleChangeUrl = e => {
    url = e.target.value
  }
  const monitorUrl = async () => {
    if(!url.trim()) return
    
    console.log({ url })
    // const newUrl = new URL(url)

    // console.log({ newUrl })

    const response = await axios(url, {
      method: 'HEAD',
      mode: 'no-cors',
      headers: {
        'Access-Control-Allow-Origin': '*',
        Accept: 'application/json',
        'Content-Type': 'application/json',
      },
      withCredentials: true,
      credentials: 'same-origin',
      crossdomain: true,
    })

    console.log(response.data)// const html = await response.text()


    // const doc = new DOMParser().parseFromString(html, 'text/html');
    // console.log(doc.title, doc.body)

    // resolved = html
  }
</script>

<!-- html -->
<h1>Web Monitor</h1>

<div class="login-buttons">
  <CustomBtn clickHandler={googleLogin}>
    Login with Google
  </CustomBtn>
  <CustomBtn clickHandler={githubLogin}>
    Login with Github
  </CustomBtn> 
</div>

<div class="url-input">
  <input
    type="url"
    placeholder="https://example.com"
    pattern="https://.*" size="30"
    required
    on:input={handleChangeUrl}
  >
  <CustomBtn clickHandler={monitorUrl}>Monitor</CustomBtn>
</div>

<div class="resolved">
  {resolved}
</div>

<!-- styles -->
<style>
  input {
    padding: 0.25rem 1rem;
  }
</style>
