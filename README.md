## TypeScript学习
    列举一些ts常用操作

# 基础类型
    声明类型
    `
    let a: boolean = false;
    let num: number = 1;
    let arr: number[] = [1,2,3];
    let b:[string,number]= ['a',1];//添加新元素只能添加string和number类型
    let c: any =1;//any可以设置成任意类型

    function d(): void {
        console.log('void表示没有任意类型，当函数没有返回值时一般设置为void')
    }
    `
类型断言
当你确切了解某值详细信息，可以使用类型断言告诉编译器，编译阶段会假设你已经确切了必须的检查
两种形式 尖括号法和as语法，两种形式等价，使用哪个全凭喜好，推荐使用as语法

    `
    let someValue: any = "this is a string";
    let strLength: number = (<string>someValue).length;//尖括号法
    let strLength: number = (someValue as string).length;//as法
    `

# 接口