### javascript 监听对象属性的变化
- 首先我们需要知道如何通过Object.defineProperty这个API来监听一个对象的变化, 注意注释里的内容!
--- 

 var temperature = undefined;
 Object.defineProperty(obj, 'temperature', {
    get: function() {
      return temperature;
    },
    set: function(value) {
      temperature = value;
    }
  });
  
---
- 当我们执行 obj.temperature =XX时，set函数就会自动调用，这为我们执行回调函数提供了契机。
- 2、
--- 
var obj = {
	watch:function(pro,callback){
		if(pro in this){
			var old = this[pro];
			Object.defineProperty(this,pro,{
				set:function(val){
					var o = old;
					old = val;
					callback(val,o,this); 
				},
				get:function(){
					return old;
				}
			});
		} else {
			throw new Error("no such property");
		}
	},
	toString:function(){
		var str = "{   ";
		for(pro in this){
          if(typeof this[pro] !== "function" ) 
          	str += (pro + " : " + obj[pro] + ",")
		}
		str[str.length-1] = ' ';
		str += " }";
		return str;
	}
}
obj.a = 3;
obj.watch("a",function(n,o,_this){ 
	console.log("new val = " + n 
			+"old val = " + o + " this is : " + (_this ));});
obj.a = 4;
---
