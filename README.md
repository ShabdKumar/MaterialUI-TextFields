## 1. Introduction

A **Text-Field** is a space where users are allowed to type any text into the app. Text-fields allow users to implement various activities on the inserted text i.e. cut, copy, paste, auto-correction, validation etc. If you click on a text-field space, it will display the keyboard.

Below is an example of a Text-field:

<img src="screenshots/textfields_simple.PNG" width="215" height="84">

Developers can add some other activities to this text-field - like error showing, all ok status with tick symbol, prefixes and suffixes etc.

## 2. Benefits

* Easier to customize.
* Error labels that display error messages when an error occurs.
* Character Counter.
* Password visibility toggle.

## 3. Typical UseCases:

MaterialText-Fields can be used in scenarios like where data needs to be gathered from users like: forms, login page etc. Below are some of the examples:

<img src="screenshots/textfields_usecase1.PNG" width="250" height="400"> <img src="screenshots/textfields_usecase2.PNG" width="250" height="400">

## 4. List of Features:

There are few features of Radio buttons listed below:

|Features|Description|
|:-:|:-:|
|Labeled/Non-Labeled|Label can be enabled and disabled for the field.|
|Assistive Elements|Elements like Helper Text and Character counter can be implemented with the field|
|Leading and Trailing Icons|Icons can be added to help user to understand the type of input expected|
|Error Message assistance|to check and verify the type of input require|
|||

Please refer below Image: 

<img src="screenshots/textfields_featuresList.PNG" width="629" height="334">

## 5. Exemplary Images:

### Defocused TextFields:

![Alt text](./screenshots/textfields_outlined-defocused.png "Outlined" )   ![Alt text](./screenshots/textfields_filled-labeled-defocused.png "Filled" )

### Focused TextFields:

![Alt text](./screenshots/textfields_filled-labeled-focused.png "Filled Labeled" )   ![Alt text](./screenshots/textfields_filled-nonlabeled-focused.png "Filled Non-labeled" )  
![Alt text](./screenshots/textfields_outlined-focused-labeled.png "Outlined Labeled" )   ![Alt text](./screenshots/textfields_outlined-focused-nonlabeled.png "Outlined Non-labeled" )

## 6. Install and Usage Instructions:

### 1. Add dependencies:

Add following to the dependencies in package.json file in entry folder of your project:

```json
{
    "dependencies": {
        "@ohos/materialtextfield": "file:../materialtextfield"
    }
}
```

### 2. Import files:

```ts
import { MaterialTextField, MaterialTextFieldOptions, MaterialTextFieldType } from "@ohos/MaterialTextField"
```

### 3. Usage:

```ts
import { MaterialTextField, MaterialTextFieldOptions, MaterialTextFieldType } from "@ohos/MaterialTextField"

@Entry
@Component
struct Outlined_sample {
  textFieldOptions: MaterialTextFieldOptions = new MaterialTextFieldOptions()
    .setIcons($r('app.media.account'), $r('app.media.clear'))
    .onTrailingIconClick((event) => {
      console.log("Trailing icon click:" + JSON.stringify(event))
    })
    .onLeadingIconClick((event) => {
      console.log("Leading icon click:" + event)
    })
    .setCharacterCounter(true, 10)
    .isValid((value) => {
      if (value.charAt(4) == 'd') {
        return { valid: true, errorMessage: '' }
      }
      else return { valid: false, errorMessage: 'd should be at 5th position' }
    })
    .setHelperText('Required*')
    .setTextInputOptions({
      placeholderText: 'mail or phone',
      input: 'Harold',
      caretColor: Color.Blue,
      fontFamily: 'cursive'
    })

  aboutToAppear() {

  }

  build() {
    Flex({
      direction: FlexDirection.Column,
      justifyContent: FlexAlign.SpaceAround,
      alignItems: ItemAlign.Center
    }) {
      MaterialTextField({
        textFieldParameters: this.textFieldOptions,
        textFieldType: MaterialTextFieldType.Outlined
      })
      TextInput({
        placeholder: 'he',
        text: 'ger'
      }).width('200vp').height('100vp').fontFamily('cursive')
    }
    .width('100%')
    .height('300vp')
    .backgroundColor(Color.White)
  }
}
```

<img src="screenshots/textfields_usage.gif" width="365" height="325">

## 7. APIs, Parameters, Options, Attributes and Events:

```ts
MaterialTextField({textFieldType:MaterialTextFieldType,textFieldParameters:MaterialTextFieldOptions})
```

### Parameters:

textFieldType: [MaterialTextFieldType](#materialtextfieldtype)

textFieldOptions: [MaterialTextFieldOptions](#materialtextfieldoptions)

### MaterialTextFieldOptions:

|Parameter|type|Remarks|
|-|-|-|
|label|string|label of textfield|
|leadingIcon|Resource|leading icon to be used|
|trailing icon|Resource|trailing icon to be used|
|characterCounter|boolean|characterCounter enabled when true|
|maxCharacters|number|max number of characters allowed|
|helperText|string|used as a hint for input text|
|textInputOptions|[Object{}](README.md#textinputoptions)|text input options|
|margin|Length or Padding|-|
|padding|Length or Padding|-|
|border|[BorderOptions](https://developer.harmonyos.com/en/docs/documentation/doc-references/ts-universal-attributes-border-0000001158261223)|-|
   
### MaterialTextFieldType:

1. Filled
2. Outlined
    
### TextInputOptions:
|Options|type|Remarks|
|-|-|-|
|id|string|id of textfield|
|input|string|input|
|placeholderText|string|placeholder of input field
|inputType|[InputType](https://developer.harmonyos.com/en/docs/documentation/doc-references/ts-basic-components-textinput-0000001233397495#EN-US_TOPIC_0000001233397495__li1018842194211)|select one of InputType
|placeholderFont|{ size?: Length, weight?:[FontWeight](https://developer.harmonyos.com/en/docs/documentation/doc-references/ts-universal-attributes-text-style-0000001111681086#EN-US_TOPIC_0000001111681086__li24391125115311), family?: string, style?: [FontStyle](https://developer.harmonyos.com/en/docs/documentation/doc-references/ts-universal-attributes-text-style-0000001111681086#EN-US_TOPIC_0000001111681086__li6906111945316)}|Font of placeholder|
|placeholderColor|Color|-|
|fontColor|Color|color of input text|
|fontSize|number|-|
|fontStyle|[FontStyle](https://developer.harmonyos.com/en/docs/documentation/doc-references/ts-universal-attributes-text-style-0000001111681086#EN-US_TOPIC_0000001111681086__li6906111945316)|-|
|fontWeight|[FontWeight](https://developer.harmonyos.com/en/docs/documentation/doc-references/ts-universal-attributes-text-style-0000001111681086#EN-US_TOPIC_0000001111681086__li24391125115311)|-|
|fontFamily|string|-|
|enterKeyType|[EnterKeyType](https://developer.harmonyos.com/en/docs/documentation/doc-references/ts-basic-components-textinput-0000001233397495#EN-US_TOPIC_0000001233397495__li1231618102427)|enter key functionality|
|caretColor|Color|color of cursor when input is being edited|
   
### Attributes:

The following attributes are supported for TextFieldOptions:

|Attribute|Description|
|-|-|
|`setTextFIeldType(type:MaterialTextFieldType)`|sets textfield type|
|`setLabel(label:string,labelWidth:number)`|sets the label for textfield|
|`setHelperText(text:string`)|sets the helper text|
|`setCharacterCounter(enable:boolean,maxCharacters:number)`|enables character counter and maximum allowed characters|
|`setIcons(leadingIcon:Resource,trailingIcon:Resource)`|sets leading and trailing icons|
|`setTextInputOptions(textInputOptions:TextInputOptions)`|sets the input text options|
|`setMargin(margin:Length or Padding)`|sets the margin for textfield|
|`setPadding(padding:Length or Padding)`|sets the padding for textfield|
|`setBorder(options:BorderOptions)`|sets the border parameters for textfield|

### Events:
|Event|Description|
|-|-|
|onLeadingIconClick(callBack:(event:[ClickEvent](https://developer.harmonyos.com/en/docs/documentation/doc-references/ts-universal-events-click-0000001111581270#EN-US_TOPIC_0000001111581270__li155675712535))=>void)|triggered when leading icon is being clicked|
|onTrailingIconClick(callBack:(event:[ClickEvent](https://developer.harmonyos.com/en/docs/documentation/doc-references/ts-universal-events-click-0000001111581270#EN-US_TOPIC_0000001111581270__li155675712535))=>void)|triggered when trailing icon is being clicked|
|onChange(callBack:(event:value?:string=>void)|triggered when textfield input changes|
|onSubmit(callBack:(enterKey?:[EnterKeyType](https://developer.harmonyos.com/en/docs/documentation/doc-references/ts-basic-components-textinput-0000001233397495#EN-US_TOPIC_0000001233397495__li1231618102427))=>void)|triggered when input of textfield is submitted|
|onEditChange(callBack:(isEditing:boolean)=>void)|triggered when user stops editing|
|isValid(callback:(value?:string)=>{})|triggered when user stops editing, should return an object of type: { valid:boolean,errorMessage:string}|

## 8. Library Features:

### Feature-1: 

***Description:*** User can define the type of textfield: *Filled* or *Outlined*.

***Code Snippet:***

```ts
build() {
    Flex({
      ...
    }) {
      Text('Filled and Labeled').fontSize('15fp').padding('5fp')
      MaterialTextField({
        textFieldParameters: this.filledLabelParas,
        textFieldType: MaterialTextFieldType.Filled
      });
      Text('Outlined and Labeled').fontSize('15fp').margin({ top: '40vp' })
      MaterialTextField({
        textFieldParameters: this.outlinedLabelParas,
        textFieldType: MaterialTextFieldType.Outlined
      });
    }.width('100%')
  }
```
***Explaination:***

Above code will create two simple Text Fields, first textfield will be type *filled* and second one will be *outlined*.

***Screenshot:***

<img src="screenshots/textfields_feature1.PNG" width="367" height="246">

<br>

### Feature-2: 

***Description:*** User can insert Label for the textfields.

***Code Snippet:***

```ts
outlinedLabelParas: MaterialTextFieldOptions = new MaterialTextFieldOptions;

aboutToAppear(): void {
    this.outlinedLabelParas = {
      ...this.outlinedLabelParas,
      label: 'User',
      .
      .
      .
    }
}
```
***Explaination:***

Above code will create a Textfield, where the label is mentioned *User*, By default it will show the label inside the Textfield but when you click on textfield to type it will appear at the top of the textfield.

***Screenshot:***

<img src="screenshots/textfields_feature2.gif" width="364" height="192">

### Feature-3: 

***Description:*** Users can insert trailing and leading icons and  bind other on-click features like drop down menu and date picker with these icons.

***Code Snippet:***

```ts
filledLabelParas: MaterialTextFieldOptions = new MaterialTextFieldOptions;

aboutToAppear() {
    this.filledLabelParas = {
      ...this.filledLabelParas,
      ...
      leadingIcon: $r("app.media.account"),
      trailingIcon: $r("app.media.clear"),
      leadingIconClick: (event) => {
        ...
      },
      trailingIconClick: (event) => {
        ...
      },
      ...
    }
}
```

***Explaination:***

Above code will create a Textfield, where icons are added at front and at end of the textfield called *Leading* and *Trainling icon* respectively. Developers can update the function to see what will happen if the user will click on these icons.

***Screenshot:***

<img src="screenshots/textfields_feature3.PNG" width="386" height="84">

### Feature-4: 

***Description:*** Users can add assistive elements like helper-text and character counter.

***Code Snippet:***

```ts
filledLabelParas: MaterialTextFieldOptions = new MaterialTextFieldOptions;

aboutToAppear() {
    this.filledLabelParas = {
      ...this.filledLabelParas,
      helperText: "Helper Text",
      characterCounter: true,
      ...
    }
}
```
***Explaination:***

Above code will create a Textfield with a helper text and character counter. Helper text will tell users what needs to be filled in the above Text Field and the character counter will count the number of characters added in Textfield.

***Screenshot:***

<img src="screenshots/textfields_feature4.PNG" width="370" height="86">

### Feature-5: 

***Description:*** User can check the validity of input given (required while validating mail-id, password format etc.) by defining callback function.

***Code Snippet:***

```ts
outlinedLabelParas: MaterialTextFieldOptions = new MaterialTextFieldOptions;

aboutToAppear() {
    this.outlinedLabelParas = {
      ...this.outlinedLabelParas,
      ...
      characterCounter: true,
      validate: (value) => {
        if (value.charAt(4) == 'd')
                return { valid: true, errorMessage: '' };
        else
                return { valid: false, errorMessage: 'd should be at 5th position' }
      },
      ...
    }
}
```

***Explaination:***

Above code will create a Textfield with some validation checks. Like for the above example: if the user will not insert d at 5th position it will give an error message like the screenshot below. 

***Screenshot:***

<img src="screenshots/textfields_feature5.gif" width="353" height="245">

### Feature-6: 

***Description:*** User can set various input-box parameters which are available in the TextInput component for open-harmony developers.

***Code Snippet:***

```ts
outlinedLabelParas: MaterialTextFieldOptions = new MaterialTextFieldOptions;

aboutToAppear() {
    this.outlinedLabelParas = {
      ...this.outlinedLabelParas,
      ...
      textInputOptions: {
        placeholderText: "eg: Harold",
        placeholderFont: {
          size: 20,
          style: FontStyle.Italic,
          weight: FontWeight.Normal
        }
      },
      ...
    }
}
```

***Explaination:***

Above code will create a Textfield with some text inputs. We can use placeholders while clicking the textfield. It will still show the details in the textfield only what type of information the user needs to provide.

***Screenshot:***

<img src="screenshots/textfields_feature6.gif" width="353" height="245">

***Note: There are more setting options for input textbox than shown (placeholderText, input and caretColor) in above code snippet. Some of those are font-style, font-weight, placeholder-font, input-type and Enter Key-type.***

## 9. Advanced features that could be implemented in Future:

Given below are suggestive features that could be implemented in future release of the library:
* Multiline input box.
* Theming of text fields.
* Addition of Voice Input
* Implementation of prefix and suffix for the input text.

## 10. Conclusion:
There are cases when a user needs to specify the type of input expected in an input field. This library is the solution for users to implement differentiating text fields with add-ons like leading and trailing icons,  helper text etc. 

## 11. Code Contribution:
If you find any problems during usage, you can submit an [Issue](https://github.com/Applib-OpenHarmony/MaterialTextFields/issues) to us. Of course, we also welcome you to send us [PR](https://github.com/Applib-OpenHarmony/MaterialTextFields/pulls).