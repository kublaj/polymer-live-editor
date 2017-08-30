# <polymer-live-editor>

`<polymer-live-editor>` is an inline code editor with a sandboxed previewer supporting multiple files. 

`<polymer-live-editor>` assumes an `index.html` file is among those in the editor. Use HTML imports
to link files to each other. 

The editor uses a `codemirror-textarea` element, which is a wrapper around <a href="https://codemirror.net/">CodeMirror</a>.

User code output is displayed in an `iframe`. It is left up to the user to specify a server
with an instance of `polymer-live-editor-server` running, using the `polymer-live-editor`'s `src` attribute.

For more information on running the `polymer-live-editor-server`, please visit the 
<a href="https://github.com/PolymerLabs/polymer-live-editor-server">`polymer-live-editor-server` repo</a>.

Example (notice one block inserts code inside a template and one directly edits the `htmlContent` property):
```html
<polymer-live-editor src="https://35.202.214.166:8080">
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
