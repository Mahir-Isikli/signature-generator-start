<template>
  <div id="app">
    <header class="header">
      <div class="container">
        <div class="inner">
          <LogoFile class="logo" />
          <h1>Email Signature Generator</h1>
       </div>
      </div>
    </header>
    <main class="main">
      <div class="container">
        <div class="inner">
          <div class="form-section">
            <h2>Enter Details</h2>
            <div class="box">
              <SignatureForm 
                :companies="companies" 
                :form="form" 
                :useCache="useCache"
              />
              <SignatureIntegrations />
            </div>
          </div>
          <div class="preview-section">
            <div class="preview-sticky">
              <h2>Signature Preview</h2>
              <SignaturePreview 
                :companies="companies" 
                :form="form"
                ref="preview"
                class="box"
              />
            </div>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
import LogoFile from './assets/logo.svg?inline'
import SignatureForm from './components/SignatureForm.vue'
import SignaturePreview from './components/SignaturePreview.vue'
import SignatureIntegrations from './components/SignatureIntegrations.vue'

export default {
  name: 'App',
  components: {
    LogoFile,
    SignatureForm,
    SignaturePreview,
    SignatureIntegrations
  },
  data() {
    return {
      useCache: window.esgConfig.useCache || true,
      companies: window.esgConfig.companies || [],
      form: {
        company: 'AdColony',
        name: '',
        jobTitle: '',
        office: '+',
        mobile: '+',
      }
    }
  }
}
</script>

<style>
body{
    margin: 0;
    padding: 0;
    font-size: 12px;
    line-height: 20px;
    color: #002848;
    font-weight: 300;
    background-color: #f8fbfe;
    font-family: 'Roboto', sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
}
.container {
    margin: 0 auto;
    padding: 0 20px;
    max-width: 1080px;
}

h1 {
    margin: 0;
    font-size: 24px;
    font-weight: 300;
    line-height: 36px;
}
h2 {
    margin: 28px 0 18px;
    font-size: 20px;
    font-weight: 700;
    line-height: 28px;
}
ol{
    margin: 0;
    padding-left: 15px;
}
ol li{
    margin-bottom: 5px;
}
ol li:last-child{
    margin-bottom: 0;
}
.spacer{
    height: 28px;
}
.box{
    border-radius: 20px;
    padding: 28px 40px 24px;
    background-color: #FFF;
    box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.05);
}
@media(max-width: 479px) {
    .box{
        padding: 20px;
    }
}

/* Button */
.btn{
    font-size: 12px;
    line-height: 16px;
    color: #f15631;
    font-weight: 700;
    padding: 8px 16px;
    position: relative;
    border-radius: 4px;
    letter-spacing: 0.01em;
    background-color: #FFF;
    transition: all .2s ease;
    text-transform: uppercase;
    border: 2px solid #f15631;
}
.btn:hover,
.btn:active{
    outline: none;
    cursor: pointer;
}
.btn:disabled{
    opacity: 0.8;
    cursor: not-allowed;
}
/* .btn:active{
    right: -2px;
    bottom: -2px;
} */
.primary-btn{
    color: #FFF;
    background-color: #F15631;
}
.primary-btn:hover,
.primary-btn:active{
    border-color: #fc7555;
    background-color: #fc7555;
}
.secondary-btn{
    color: #f15631;
    background-color: #FFF;
}
.secondary-btn:hover,
.secondary-btn:active{
    color: #fc7555;
    border-color: #fc7555;
}

/* Header */
.header {
    color: #fff;
    background-color: #163f5f;
    background: linear-gradient(125.85deg, #214A6A 29.73%, #002848 98.42%);
}
.header .inner {
    padding: 20px 0 10px;
}
@media (max-width: 767px) {
    .header .inner h1{
        font-size: 20px;
    }
}
@media (min-width: 768px) {
    .header .inner {
        display: flex;
        padding: 36px 0;
        align-items: center;
        justify-content: space-between;
    }
}
.header .logo {
    height: 40px;
}
.header .logo .icon-text path {
    fill: #FFF;
}

/* Main */
.main{
    margin: 24px 0 50px;
}
.main .form-section{
    width: 480px;
    max-width: 100%;
}
.main .preview{
    min-width: 450px;
}
@media (max-width: 919px) {
    .main .preview-section{
        margin-top: 20px;
        overflow: hidden;
        overflow-x: auto;
    }
    .preview-sticky{
        margin-bottom: 20px;
    }
}
@media (min-width: 920px) {
    .main .inner{
        display: flex;
    }
    .main .form-section{
        margin-right: 20px;
    }
    .main .preview-section{
        max-width: 580px;
    }
    .preview-sticky{
        top: 20px;
        position: sticky;
    }
}
</style>
