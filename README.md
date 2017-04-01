#### js算法
 * 1 递归
 
 
###### 递归
 * 实现js Object 的复制 
   据我们所知，obj 属于引用类型 
   ==》 obj 和 arr 在变量赋值的时候并不是新建一个 Object 而是将 this 指向那个 堆
   即 ==》 堆改变 则 this 改变 
        ==》 obj 改变
   那么我们要实现复制 obj 和 arr 就需要通过 copy 表层属性， 我们用递归算法来实现这个结果
 ``` js
function extend(obj,bool){  // bool 是否深度复制
  let news={},
      bool = bool || false;
  if(!{}.toString.call(obj)=='[object Object]') {   // 不是对象的时候 直接返回出去
    console.log('The is not Obj')
    return obj 
  }
  if(bool){
    news.__proto__ = obj.__proto__
  }
  for(let key in obj){
    if({}.toString.call(obj[key])=='[object Object]'){
       news[key] = extend(obj[key])  //  如果属性中也是对象的话  进行递归算法
    }else{
       news[key] = obj[key]
    }
  }
return news
}
 ```
