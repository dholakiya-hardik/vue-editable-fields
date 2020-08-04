# vue-editable-fields

## Installation
### Using npm
```
npm i vue-editable-fields

```
### Import 

```
import  VueEditableFields from "vue-editable-fields"
```
### Globle use

```
Vue.use(VueEditableFields)
```
### Use in component
Add below code in components property 

```
VueEditableFields
```
### Add tag in template 
```
<VueEditableFields/>
```

#### Prop List 
| Prop       | Type     | Required |
| ---------- | --------:| --------:|
| inputValue | String   | No       |
| classes    | String   | No       |
| isNumeric  | Boolean  | No       |
| isMutiLine | Boolean  | No       |

#### Text fields events

| Events     | return   
| ---------- | --------:
| input      | String    
| save       | String  