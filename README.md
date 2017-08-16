# \<polymer-live-editor\>

`polymer-live-editor` is an inline code editor and previewer supporting multiple files. 

Example (notice one block inserts code inside a template and one directly edits the `htmlContent` property):
```html
<polymer-live-editor src="http://localhost:3000">
  <polymer-live-editor-tab tab-name="custom-element.html" id="customel">
    <div slot="heading">
      custom-element.html
    </div>
    <template slot="html-content"></template>
  </polymer-live-editor-tab>
  <polymer-live-editor-tab tab-name="index.html">
    <div slot="heading">
      index.html
    </div>
    <template slot="html-content">
      <script src="https://polygit.org/components/webcomponentsjs/webcomponents-loader.js"></script>
      <link rel="import" href="custom-element.html">
      <custom-element></custom-element>
    </template>
  </polymer-live-editor-tab>
</polymer-live-editor>

<script>
  var htmlContent = `<link rel="import"  href="https://polygit.org/components/polymer/polymer-element.html">
    <script>
      // Define the class for a new element called custom-element
      class CustomElement extends Polymer.Element {
        static get is() { return "custom-element"; }
        constructor() {
            super();
            this.textContent = "I'm a custom-element.";
          }
      }
      // Register the new element with the browser
      customElements.define(CustomElement.is, CustomElement);
    <`;
  htmlContent += '/script>';
  document.querySelector('#customel').htmlContent = htmlContent;
</script>
```
