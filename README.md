# v-data-form

A vue form whose UI and behaviour are only determined by the data input in it.

## Dependencies

1. [Vuejs +v2.6.10](https://vuejs.org)
2. [Vuetify +v1.5.5](https://vuetifyjs.com)

## Usage

__Don't use just yet. We are still building!__

### Installation

1. You can get this as an NPM package in your app

    ```bash
    npm install --save v-data-form
    ```

2. Go to your ```main.js``` or whatever entry file you use for you project and import v-data-form

    ```Javascript
    import 'v-data-form'
    ```

3. In any of your component templates, just use the ```<v-data-form></v-data-form>``` tags e.g.

    ```html
    <v-data-form form-data="yourData"></v-data-form>
    ```

### Data Schema

The form receives props:

- formData ('form-data' in template syntax)
- style
- submissionHandler (submission-handler in template syntax)
- cancellationHandler (cancellation-handler in template syntax)
- submissionButtonLabel (submission-button-label in template syntax)
- cancellationButtonLabel (cancellation-button-label in template syntax)

```JavaScript
const props = {
  formData: [ // Array of objects with properties; 'type', 'name', 'value', 'options'
    /* e.g.
    {
      type: "text-field", value: "hello world", name: 'greetingInput',
      options: {
        style: {color: "blue"},
        onclick: () => alert('clicked')
      }
    },
    {
      type: "autocomplete", value: "", name: 'district',
      options: {
        items: ['Hoima', 'Kampala', 'Wakiso'],
      }
    },
    */
  ],
  styleObj: { // CSS style
    /*e.g.
    "background-color": "#fff"
    */
  },
  submissionHandler: (formOutput) => {
    /* Do Something on submission
    (i.e. after SUBMIT button is clicked)*/
    /* formOutput is the data output of the form:
    It is kind like the form-data that is sent to the server
    by HTML forms using the signature {[nameOfInput: string]: value}
    */
  },
  cancellationHandler: (formOutput) => {
    /* Do something on cancellation
    (i.e. after CANCEL button is clicked)*/
    /* formOutput is the data output of the form:
    It is kind like the form-data that is sent to the server
    by HTML forms using the signature {[nameOfInput: string]: value}
    */
  },
  submissionButtonLabel: '', // Defaults to 'submit'
  cancellationButtonLabel: '', // Defaults to 'cancel'
}
```

Each item in the 'formData' property (shown above), must have at least two properties; the __type__ and the __name__:

<dl>
<dt><strong>type</strong></dt>
<dd>
This is the name of the type of element to render. It can be any of the following:

- 'text-field'
- 'textarea'
- 'select'
- 'autocomplete'
- 'button'

More are being added to the list.
</dd>
<dt><strong>name</strong></dt>
<dd>
This is the unique name of that element. It is the key while the element's value is the value in the <strong>formOut</strong> property (see the output section) of the form.
</dd>
</dl>

It can also have two other properties; __value__ and __options__

<dl>
<dt><strong>value</strong></dt>
<dd>
This is the initial value of the rendered element.
<br />
<br />
The data type depends on the element type e.g. for type: 'textarea', the value should be a string while type: 'text-field' could be a number if in the options, there is a property 'type': 'number'
</dd>

<dt><strong>options</strong></dt>
<dd>
This contains any extra props to add to the rendered element. It should be an object of signature {[prop: string]: any}
<br />
<br />
To get the possible props for any given element type, search for that type on the <a href="https://vuetifyjs.com/en/components/api-explorer" target="_blank">vuetify component explorer</a>.
</dd>
</dl>

### Output

The form has a property called ```formOutput``` which is an object holding the values of each element in the form, the keys being the names of those elements.

For example, basing on the example 'formData' property of the props in the code section under 'Data Schema', here is the formOutput

```JavaScript
const formOutput = {
  greetingInput: 'hello world',
  district: 'Kampala', // In case the user selected Kampala
}
```

__The formOutput is accessible to the submissionHandler and cancellationHandler prop functions.__

## Acknowledgements

[Vuetify](https://vuetifyjs.com) is the component library this form is based on.

This [post by Divyam Rastogi](https://medium.com/justfrontendthings/how-to-create-and-publish-your-own-vuejs-component-library-on-npm-using-vue-cli-28e60943eed3) was very helpful when publishing to NPM.

## License

Copyright (c) 2019 [Martin Ahindura](https://github.com/Tinitto)
Licensed under the [MIT License](./LICENSE)
