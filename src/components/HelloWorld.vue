<template>
  <div>
    <h1>Formulario</h1>

    <div>
      <label for="">Nome:</label>
      <input type="text" v-model="name" />
    </div>

    <div>
      <label for="">Cargo</label>
      <input type="text" v-model="occupation" />
    </div>
  </div>

  <h1>Preview</h1>
  <div class="card" ref="preview">
    <div>
      <div class="image">
        <img
          src="https://raw.githubusercontent.com/johnathansantos/ultravel-assinatura-email/main/src/assets/signature-animation.gif"
          alt=""
        />
      </div>
      <div class="name">{{ name }}</div>
      <div class="occupation">{{ occupation }}</div>
      <div class="details">
        <div class="social">
          <div>
            <span>
              <img
                src="https://raw.githubusercontent.com/johnathansantos/ultravel-assinatura-email/main/src/assets/phone-call.png"
                alt=""
              />
            </span>
            (48) 4141-2113
          </div>
          <div>
            <span>
              <img
                src="https://raw.githubusercontent.com/johnathansantos/ultravel-assinatura-email/main/src/assets/internet-connection.png"
                alt=""
              />
            </span>
            ultravel.com.br
          </div>
          <div>
            <span>
              <img
                src="https://raw.githubusercontent.com/johnathansantos/ultravel-assinatura-email/main/src/assets/instagram.png"
                alt=""
              />
            </span>
            ultravelbrasil
          </div>
        </div>
        <div>
          <span>
            <img
              src="https://raw.githubusercontent.com/johnathansantos/ultravel-assinatura-email/main/src/assets/pin.png"
          /></span>
          R. Santos Saraiva, 238 - Loja 7 - Estreito - Florianópolis - SC
        </div>
      </div>
    </div>
  </div>

  <div @click="download">Download</div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      name: 'Bernardo Pereira',
      occupation: 'gerente comercial',
    };
  },
  methods: {
    download: function () {
      let el = this.$refs.preview;
      console.log(this.$refs);

      let style = `<style type="text/css"> body{background: #efefef; font-family: 'Bai Jamjuree', sans-serif;}.card-wrapper{background: #efefef; padding: 20px; width: 700px;}.card{background-color: #fff; /*box-shadow: 0 10px 10px 0 #ccc;*/ width: 350px; border-radius: 10px; padding: 10px}.card .image{display: flex; justify-content: center; border: 1px solid #efefef; border-radius: 10px}.card .image>img{max-width: 100%;}.card .name{font-size: 20px; font-weight: bold; margin-top: 5px}.card .occupation{text-transform: uppercase; font-size: 10px; letter-spacing: 4px}.card .details{font-size: 12px; margin-top: 10px}.card .details span > img{width: 10px; height: 10px; margin-right: 4px}.card .social{display: flex; justify-content: space-between; margin-bottom: 4px}</style>`;

      let html = `<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
              "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"><html> <head>
          <meta http-equiv="Content-Type" content="text/html charset=UTF-8"/>
          <link rel="preconnect" href="https://fonts.googleapis.com">
          <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
          <link href="https://fonts.googleapis.com/css2?family=Bai+Jamjuree:wght@400;700&display=swap" rel="stylesheet">
          ${style} </head> </html> <body> ${el.outerHTML} </body>
      `;

      console.log(html);

      let content = html;
      let mimeType = 'text/html';
      let filename =
        this.name.toLowerCase().replace(' ', '-') + 'signature.html';

      const a = document.createElement('a'); // Create "a" element
      const blob = new Blob([content], { type: mimeType }); // Create a blob (file-like object)
      const url = URL.createObjectURL(blob); // Create an object URL from blob
      a.setAttribute('href', url); // Set "a" element link
      a.setAttribute('download', filename); // Set download filename
      a.click(); // Start downloading
    },
  },
};
</script>

<style scoped lang="scss" ref="aaa">
body {
  background: #efefef;
  font-family: 'Bai Jamjuree', sans-serif;
}

.card-wrapper {
  background: #efefef;
  padding: 20px;
  width: 700px;
}

.card {
  background-color: #fff;
  /*box-shadow: 0 10px 10px 0 #ccc;*/
  width: 350px;
  border-radius: 10px;
  padding: 10px;

  .image {
    display: flex;
    justify-content: center;
    border: 1px solid #efefef;
    border-radius: 10px;
    & > img {
      max-width: 100%;
    }
  }

  .name {
    font-size: 20px;
    font-weight: bold;
    margin-top: 5px;
  }

  .occupation {
    text-transform: uppercase;
    font-size: 10px;
    letter-spacing: 4px;
  }

  .details {
    font-size: 12px;
    margin-top: 10px;
  }

  .details span > img {
    width: 10px;
    height: 10px;
    margin-right: 4px;
  }

  .social {
    display: flex;
    justify-content: space-between;
    margin-bottom: 4px;
  }
}
</style>
