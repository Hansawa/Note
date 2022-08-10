1. 模块化编程export和import

export：用于规定模块的对外接口
```js
/* 文件1 */
/*export*/
/* default整个文件只能有一个，在import时取别名 */
export default function () {

};
function x() {

}

class person{
    constructor(){

    }
}
export let a = 0;
export {x, person}
/* 文件2 */
import {x, person} from '文件1'
/*import {x as othername} from ''*/
/*import * as othername from ''*/
x(xxx);
person
```

import：用于导入其他模块提供的功能