<template>
  <body>
    <section class="card-base">
      <div class="row">
        <div
          class="img-sec col d-flex justify-content-center align-items-center"
        >
          <div>
            <div
              class="parentDiv w-100 d-flex justify-content-center position-relative"
              id="image"
            >
              <img
                :src="imageSrc"
                class="image-main border-0 m-0"
                alt="sample"
              />
              <p
                :style="[
                  { left: lPosition + 'px' },
                  { top: tPosition + 'px' },
                  { 'font-size': fontSize + 'px' },
                  { opacity: Opacity },
                  { transform: `rotate(${this.rotatex}deg)` },
                ]"
                :class="[
                  fontEffect,
                  selectedFont,
                  { italic: isItalic },
                  { bold: isBold },
                  { underline: isUnderline },
                ]"
                class="input-text position-absolute"
              >
                {{ link }}
              </p>
            </div>

            <div class="d-flex d-inline my-4 mx-4 d-none">
              <h6 class="my-2 lead">export image</h6>
              <a href="#">
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="23"
                  height="23"
                  fill="currentColor"
                  class="bi bi-download mx-3 my-2"
                  viewBox="0 0 16 16"
                >
                  <path
                    d="M.5 9.9a.5.5 0 0 1 .5.5v2.5a1 1 0 0 0 1 1h12a1 1 0 0 0 1-1v-2.5a.5.5 0 0 1 1 0v2.5a2 2 0 0 1-2 2H2a2 2 0 0 1-2-2v-2.5a.5.5 0 0 1 .5-.5z"
                  />
                  <path
                    d="M7.646 11.854a.5.5 0 0 0 .708 0l3-3a.5.5 0 0 0-.708-.708L8.5 10.293V1.5a.5.5 0 0 0-1 0v8.793L5.354 8.146a.5.5 0 1 0-.708.708l3 3z"
                  />
                </svg>
              </a>
            </div>
            <button
              class="btn btn-primary w-100 mt-4"
              @click="export_image"
              type="button"
            >
              Export image
            </button>
          </div>
        </div>
        <div class="tabs-sec col">
          <div class="row">
            <div class="tabs col-12 pX-3 py-3">
              <div class="container">
                <ul class="nav nav-tabs">
                  <li class="nav-item">
                    <a
                      class="nav-link active"
                      href="#Text"
                      id="login-tab"
                      data-bs-toggle="tab"
                      >Text</a
                    >
                  </li>
                  <li class="nav-item">
                    <a
                      class="nav-link"
                      href="#Image"
                      id="register-tab"
                      data-bs-toggle="tab"
                      >Image</a
                    >
                  </li>
                </ul>
                <!-- textTab -->
                <div class="tab-content mt-1">
                  <div id="Text" class="tab-pane active">
                    <!-- textInput -->
                    <div>
                      <label>Text : </label>
                      <input
                        type="text"
                        class="text-input mt-4 mx-3 border rounded-2 w-50"
                        placeholder=" link address"
                        v-model="link"
                      />
                    </div>
                    <br />
                    <!-- fontSize -->
                    <div class="d-flex d-inline">
                      <label>Font Size : </label>
                      <input
                        v-model="fontSize"
                        style="margin-left: 20px"
                        type="range"
                        min="0"
                        max="115"
                        class="mt-2"
                      />
                    </div>
                    <br />

                    <!-- fontStyles -->
                    <div class="d-flex d-inline">
                      <label> Styles : </label>
                      <div class="d-flex justify-content-evenly mx-3">
                        <div class="form-check mx-3">
                          <input
                            v-model="isItalic"
                            class="form-check-input"
                            type="checkbox"
                            id="flexCheckDefault"
                          />
                          <label
                            class="form-check-label"
                            for="flexCheckDefault"
                          >
                            Italic
                          </label>
                        </div>
                        <div class="form-check mx-3">
                          <input
                            v-model="isBold"
                            class="form-check-input"
                            type="checkbox"
                            id="flexCheckDefault"
                          />
                          <label
                            class="form-check-label"
                            for="flexCheckDefault"
                          >
                            Bold
                          </label>
                        </div>
                        <div class="form-check mx-3">
                          <input
                            v-model="isUnderline"
                            class="form-check-input"
                            type="checkbox"
                            id="flexCheckDefault"
                          />
                          <label
                            class="form-check-label"
                            for="flexCheckDefault"
                          >
                            Underline
                          </label>
                        </div>
                      </div>
                    </div>
                    <br />
                    <!-- fontBox -->
                    <div class="d-flex justify-content-between">
                      <!-- fonts -->
                      <div class="fontsSec">
                        <label class="mb-2">Fonts : </label>
                        <div>
                          <select
                            v-model="selectedFont"
                            class="rounded-2 border"
                          >
                            <option value="font11">Arial</option>
                            <option value="font1">Sofia</option>
                            <option value="font2">Trirong</option>
                            <option value="font3">Audiowide</option>
                            <option value="font4">Brush Script MT</option>
                            <option value="font5">Courier New</option>
                            <option value="font6">Garamond</option>
                            <option value="font7">Georgia</option>
                            <option value="font8">Times New Roman</option>
                            <option value="font9">Trebuchet MS</option>
                            <option value="font10">Tahoma</option>
                          </select>
                        </div>
                      </div>
                      <!-- fontEffect -->
                      <div class="fontsStyleSec">
                        <label class="mb-2">Font Effects : </label>
                        <div>
                          <select v-model="fontEffect" class="rounded-2 border">
                            <option value="">no effect</option>
                            <option value="font-effect-neon">Neon</option>
                            <option value="font-effect-outline">Outline</option>
                            -->
                            <option value="font-effect-emboss">Emboss</option>
                            <option value="font-effect-shadow-multiple">
                              Multiple Shadow
                            </option>
                            <option value="font-effect-fire">Fire</option>
                          </select>
                        </div>
                      </div>
                    </div>

                    <br />
                    <!-- opacityStyle -->
                    <div class="d-flex d-inline">
                      <label>Opacity : </label>
                      <input
                        v-model="Opacity"
                        style="margin-left: 20px"
                        type="range"
                        min="0"
                        max="1"
                        step="0.1"
                      />
                    </div>
                    <br />
                    <!-- rotate -->
                    <div class="d-flex d-inline">
                      <label>Rotate : </label>
                      <input
                        v-model="rotatex"
                        class="mx-3"
                        type="range"
                        min="0"
                        max="360"
                      />
                    </div>
                    <br />
                    <!-- leftPosition -->
                    <div class="d-flex d-inline">
                      <label>Left Position : </label>
                      <input
                        v-model="lPosition"
                        class="mx-3"
                        type="range"
                        min="0"
                        max="350"
                      />
                    </div>
                    <br />
                    <!-- topPosition -->
                    <div class="d-flex d-inline">
                      <label>Top Position : </label>
                      <input
                        v-model="tPosition"
                        class="mx-3"
                        type="range"
                        min="0"
                        max="350"
                      />
                    </div>
                  </div>
                  <!-- imageTab -->
                  <div id="Image" class="tab-pane fade">
                    <input
                      @change="changeUploadImage"
                      class="input_container w-100 mt-4"
                      type="file"
                    />
                  </div>
                  <!-- watermarkTab -->
                  <div id="watermark" class="tab-pane fade"></div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </body>
</template>

<script>
import html2canvas from "html2canvas";
export default {
  name: "App",
  data() {
    return {
      imageSrc: "../../sample.jpeg",
      selectedFont: "",
      selectedFontStyle: "",
      link: "",
      fontSize: 18,
      isItalic: false,
      isBold: false,
      isUnderline: false,
      Opacity: 1,
      rotatex: 0,
      lPosition: 0,
      tPosition: 0,

      fontEffect: {
        "font-effect-fire": false,
        "font-effect-neon": false,
        "font-effect-outline": false,
        "font-effect-emboss": false,
        "font-effect-shadow-multiple": false,
      },
    };
  },
  methods: {
    changeUploadImage(event) {
      let files = event.target.files;
      const reader = new FileReader();
      const file = files[0];
      let rawImg;
      reader.onloadend = () => {
        rawImg = reader.result;
        this.imageSrc = rawImg;
      };

      reader.readAsDataURL(file);
    },
    export_image() {
      const div = document.querySelector("#image");
      this.getScreenshotOfElement(div);
    },
    async getScreenshotOfElement(element) {
      const canvas = await html2canvas(element);
      console.log(canvas.toDataURL("image/jpeg"));
      this.download(canvas.toDataURL("image/jpeg"), this.link, "image/jpeg");
      console.log(file);
    },
    download(data, filename, type) {
      var block = data.split(";");
      // Get the content type of the image
      var contentType = block[0].split(":")[1]; // In this case "image/gif"
      // get the real base64 content of the file
      var realData = block[1].split(",")[1]; // In this case "R0lGODlhPQBEAPeoAJosM...."
      var file = this.b64toBlob(realData, contentType);
      if (window.navigator.msSaveOrOpenBlob)
        // IE10+
        window.navigator.msSaveOrOpenBlob(file, filename);
      else {
        // Others
        var a = document.createElement("a"),
          url = URL.createObjectURL(file);
        a.href = url;
        a.download = filename;
        document.body.appendChild(a);
        a.click();
        setTimeout(function () {
          document.body.removeChild(a);
          window.URL.revokeObjectURL(url);
        }, 0);
      }
    },
    b64toBlob(b64Data, contentType, sliceSize) {
      contentType = contentType || "";
      sliceSize = sliceSize || 1080;

      var byteCharacters = atob(b64Data);
      var byteArrays = [];

      for (
        var offset = 0;
        offset < byteCharacters.length;
        offset += sliceSize
      ) {
        var slice = byteCharacters.slice(offset, offset + sliceSize);

        var byteNumbers = new Array(slice.length);
        for (var i = 0; i < slice.length; i++) {
          byteNumbers[i] = slice.charCodeAt(i);
        }

        var byteArray = new Uint8Array(byteNumbers);

        byteArrays.push(byteArray);
      }

      var blob = new Blob(byteArrays, { type: contentType });
      return blob;
    },
  },
};
</script>

<style></style>
