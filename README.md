# TypeScript学习
    列举一些ts常用操作

## 基础类型
### 声明类型

 ```
    let a: boolean = false;
    let num: number = 1;
    let arr: number[] = [1,2,3];
    let b:[string,number]= ['a',1];//添加新元素只能添加string和number类型
    let c: any =1;//any可以设置成任意类型

    function d(): void {
        console.log('void表示没有任意类型，当函数没有返回值时一般设置为void')
    }
 ```
### 类型断言
当你确切了解某值详细信息，可以使用类型断言告诉编译器，编译阶段会假设你已经确切了必须的检查
两种形式 尖括号法和as语法，两种形式等价，使用哪个全凭喜好，推荐使用as语法

    ```
    let someValue: any = "this is a string";
    let strLength: number = (<string>someValue).length;//尖括号法
    let strLength: number = (someValue as string).length;//as法
    ```

## 接口
### interface
LabelledValue接口好比一个名字，用户来描述例子的要求，代表有一个label属性并且类型为string的对象
```
interface LabelledValue {
    label: string;
}
function printLabel(labelledObj: LabelledValue) {
  console.log(labelledObj.label);
}

let myObj = {size: 10, label: "Size 10 Object"};
printLabel(myObj);
```
### 可选属性
接口里的属性不全都是必需的。 有些是只在某些条件下存在，或者根本不存在。可选属性在应用"option bags"模式时很常用
```
interface SquareConfig {
  color?: string;
  width?: number;
}

function createSquare(config: SquareConfig){
  let newSquare = {color: "white", area: 100};
  if (config.color) {
    newSquare.color = config.color;
  }
  if (config.width) {
    newSquare.area = config.width * config.width;
  }
  return newSquare;//{color: "black",area: 100}
}

let mySquare = createSquare({color: "black"});
```

### 只读属性
赋值后 x再也不能改变，interface弥补const声明对象中，对象的可改变。
```
interface Point {
    readonly x: number;
}
let a:Point = {x:1};
```
ts具有ReadonlyArray<T>类型，可确保数组创建后再也不能修改
```
let a: ReadonlyArray<number> = [1,2,3];
a[0]=2// error!
```
