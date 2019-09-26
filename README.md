接口：
  interface GenericIdentityFn {
    <T>(arg: T): T;
  }

泛型：不同于any 不会丢失信息
  function identify<T>(arg:T):T {
    return arg
  }
  
交叉类型：&叠加
联合类型：|或
类型保护就是一些表达式，它们会在运行时检查以确保在某个作用域里的类型。 要定义一个类型保护，我们只要简单地定义一个函数，它的返回值是一个 类型谓词：
function isFish(pet: Fish | Bird): pet is Fish {
    return (<Fish>pet).swim !== undefined;
}


 # Typescript与Javascript共享相同的基本类型，但有一些额外的类型。
    元组 Tuple: 要以正确的顺序预定义数据类型
      const messyArray = [' something', 2, true, undefined, null];
      const tuple: [number, string, string] = [24, "Indrek" , "Lasn"]
    枚举 enum:
      enum Color {Red = 1, Green = 2, Blue = 4}
      let c: Color = Color.Green;
      let colorName: string = Color[2];
    Any 与Void:
      在Ts中，你必须在函数中定义返回类型,否则会报错；将其返回值定义为void,将无法 return
  
 # 自定义类型：Interface（接口） vs Type alias（类型别名）
  相同点：都可以用来描述一个对象或函数；都允许拓展（extends）
  不同点：
    type 可以声明基本类型别名，联合类型，元组等类型：type Name = string
    type 语句中还可以使用 typeof获取实例的 类型进行赋值：type B = typeof div
    interface 能够声明合并：
    
      interface User {
        name: string
        age: number
      }
      interface User {
        sex: string
      }
    interface 有可选属性和只读属性：
      interface Person {
        readonly loginName: string;
        name: string;
        age?: number;
        gender?: number;
      }
  # 实现与继承：implements vs extends
    
    interface IDeveloper {
       name: string;
       age?: number;
    }
    // OK
    class dev implements IDeveloper {
        name = 'Alex';
        age = 20;
    }
    // OK
    class dev2 implements IDeveloper {
        name = 'Alex';
    }
    // Error
    class dev3 implements IDeveloper {
        name = 'Alex';
        age = '9';
    }
    
 # 声明文件与命名空间：declare 和 namespace
    declare：当使用第三方库时，我们需要引用它的声明文件，才能获得对应的代码补全、接口提示等功能。
    
      declare var 声明全局变量
      declare function 声明全局方法
      declare class 声明全局类
      declare enum 声明全局枚举类型
      declare global 扩展全局变量
      declare module 扩展模块
