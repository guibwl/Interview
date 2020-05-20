<!--
 * @Date: 2020-05-20 14:16:10
 * @LastEditors: Jack Deng
 * @LastEditTime: 2020-05-20 14:17:05
 * @FilePath: /Interview/interview.md
--> 
##前端面试
- 使用JS实现一个搜索二叉搜索树


//二叉树
function BST() {
	this.root = null;

	function _node(key) {
		return {
			key: key,
			left: null,
			right: null
		}
	}

	//插入节点
	this.insert = function(key){

		let node = _node(key);

		if(this.root === null) {
			this.root = node;
			return;
		}

        let buffer = this.root;

        while(true) {

            if(node.key > buffer.key) {
                if(buffer.right === null) {
                    buffer.right = node;
                    break;
                } else {
                    buffer = buffer.right;
                }
            }

            if(node.key <= buffer.key) {
                if(buffer.left === null) {
                    buffer.left = node;
                    break;
                } else {
                    buffer = buffer.left;
                }
            }
        }
    }
}

let bst = new BST();
bst.insert(24);
bst.insert(45);
bst.insert(16);
bst.insert(4);
bst.insert(6);
bst.insert(66);
bst.insert(22);

console.log(bst.root);


- 手写一个debounce函数

function debounce(fn, delay) {

     let timer;
     
     return function () {
       
       clearTimeout(timer);

       timer = setTimeout(() => {
         fn.apply(this, arguments);
       }, delay);
     }
}


- 请列举出你觉得为什么React比vanillaJS好用的原因

1,不直接操作dom，因为渲染过程要慢于js执行速度，而且渲染线程和js线程互斥，频繁操作dom也导致频繁切换线程影响性能，而react则是将要渲染的一批虚拟dom过滤出来（涉及fiber、diff算法等优化），一次提交到浏览器渲染；

2,组件化思路，更加利于封装抽象，分层设计，有利于后面重复利用代码，提升开发效率，利于应用维护。

3,灵活性，React只是MVC中的View层，自己无法构建大型的应用，需要与已有的框架和库来配合，如：、Redux（状态管理）、Axios/Fetch（异步请求）等。
