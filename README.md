<font color=#0099ff size=12 face="黑体">

#### js算法
 * 1 [递归](#递归)
 * 2 [冒泡](#冒泡)
 * 3 [快速](#优先排序)

 
 
 
 
 
###### 递归
 * 实现js Object 的复制 
 
   据我们所知，obj 属于引用类型 
   
   ==> obj 和 arr 在变量赋值的时候并不是新建一个 Object 而是将 this 指向那个 堆
   
   即 ==> 堆改变 则 this 改变 
   
        ==> obj 改变
        
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
 
 ###### 冒泡
 * 实现js Array 的排序 
   
   目前来说 常见冒泡方式
   
   1. 事件冒泡
   
   2. 排序冒泡
   
   我们以 arr 排序作为案例来说明
   
 ``` js
 function sort(arr){  // 就像气泡一样 
   var i=0,j,k,l=arr.length;
     for(i;i<l-1;i++){
       for(j=i+1;j<l;j++){
         if(arr[i]>arr[j]){
           k = arr[j];
           arr[j] = arr[i];
           arr[i] = k;
         }
       }
     }
   return arr
 }
 var arr = [1,4,8,81,64,56,1,316,4564,1];
 sort(arr) //[1, 1, 1, 4, 8, 56, 64, 81, 316, 4564]
 ```
 </font>
 
  ###### 快速排序
 * 实现js Array 的排序 
   
   目前来说 常见排序方式
   
   1. 暴力破解（不考虑内存和速度）
  
   2. 排序冒泡（减少 O^N）
   
   3. 快速排序 （ 在数据量大的时候比冒泡稳定 ， 具体速度仍要看数组无序程度， 比如完全反序数组和冒泡的速度是等同的）
   
   4. 归并排序 （ 分治算法的分支？ 需要开辟多个空间来完成，理论上是将问题简化然后再分步解决 ）
   我们以 arr 排序作为案例来说明
   
 ``` js
function sort(arr){
  let i=0,l=arr.length;
  for(i;i!=l-1;i++){
    let j = i;
    while(arr[j]<arr[j+1] || j==1){
      let k = arr[j]
      arr[j] = arr[j+1]
      arr[j+1] = k
      j--;
    }
  }
  console.log(arr.reverse())
}
 var arr = [1,4,8,81,64,56,1,316,4564,1];
 sort(arr) //[1, 1, 1, 4, 8, 56, 64, 81, 316, 4564]
 ```
 </font>

