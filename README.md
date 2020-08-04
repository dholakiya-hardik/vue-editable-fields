# vue-editable-fields

## Installation
### Using npm
```
npm i vue-editable-fields

```
### Import 

```
import  {Textbox, Selectbox} from "vue-editable-fields"
```
### Globle use

```
Vue.use(Textbox)
Vue.use(Selectbox)
```
### Use in component
Add below code in components property 

```
Textbox, Selectbox
```
### Add tag in template 
```
<Textbox/>
<Selectbox>
```

#### Textbox Prop List 
| Prop       | Type     | Required |
| ---------- | --------:| --------:|
| inputValue | String   | No       |
| classes    | String   | No       |
| isNumeric  | Boolean  | No       |
| isMutiLine | Boolean  | No       |

#### Textbox fields events

| Events     | return   
| ---------- | --------:
| input      | String    
| save       | String  



#### Selectbox Prop List 
| Prop               | Type             | Required |
| ------------------ | ----------------:| --------:|
| selectedOption     | String           | No       |
| options            | Array            | No       |
| showDefaultOption  | Boolean          | No       |
| classes            | String or Array  | No       |
| defaultOptionLabel | String           | No       |

#### Selectbox fields events

| Events       | return   
| ------------ | --------:
| selectOption | String    
| save         | String  