# Vue Js Counter


![altcenter](https://www.mustafacagri.com/wp-content/uploads/2020/10/VueJsCounter.gif "Vue Js Counter")


With the Vue Js Counter, you can count up or down between two numbers.

For example, you can count down from 2020 to 1980 or count up from 1900 to 1999.

## Setup

```npm install vue-js-counter```

## Import
```<script>
import VueJsCounter from 'vue-js-counter'
    export default {
        components: {
            VueJsCounter 
        }
    }
</script>
```

## Usage (Count Up)
```
<VueJsCounter start="1900" end="1999" duration="5000" thousand="." decimal=","></VueJsCounter>
```


## Simple Usage (Count Up)
```
<VueJsCounter end="2020"></VueJsCounter>
```


## Usage (Count Down)
```
<VueJsCounter start="2020" end="1900"></VueJsCounter>
```

## Notes
Only **end** attribute is required. The others are optional.

If **start** attribute is not filled, Vue Js Counter understands that it will be count up to **end** value.

If **end** is smaller than **start** value, it will be counted down **end** to **start**.



## Attributes
`start (optional)`: The starting number. If you leave it blank, ***default value is 0***.

**`end (required)`**: The ending number.

`duration (optional)`: Specifies how long the count down / up will takes in millisecond. ***default value is 2000***.

`thousand (optional)`: Specifies the character of the thousands separator. ***default value is . (dot)***.

`thousand (optional)`: Specifies the character of the decimal separator. ***default value is , (comma)***.