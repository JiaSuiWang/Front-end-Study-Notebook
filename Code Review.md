# Code Review

1.**用ESlint来做code review** 快捷键 **shift + alt + F**

2.form表单只有一个，多个输入用的是input tag

3.多个input和它的标签用div封装起来

4.如果有没有用到的attribute，就删除掉

5.如果有没有用到的依赖，就删除掉

6.这里取名叫event，不要叫别的

```typescript
onChange={(event) => { handleChange(event, 'speed') }}
```



7.每一个attribute都占一行

### 8.接口里面的变量声明用分号隔开

9.调用component的时候，里面传入的attribute，每个attribute占一行

10.component的返回类型不用标注：JXS Element，因为也只有这种类型



# 11命令要用yarn不用npm，

​	得到npm的方法是load.js自带npm

​	得到yarn的方法是 npm install yarn -g，这里的g代表全局变量



12css是全局的只用引入一次

​	css在.tsx文件里面的引入方式是`import 'antd/dist/antd.css';`

 	而在.css文件里面引入的方式是`@import '~antd/dist/antd.css';`

​		  有~代表着要去node_module 下面找

​		没有~表示直接引入

3.养成随时保存的好习惯，如果vs文件上方有小圆点，就代表没有保存







# effectState一般在数据查询以及少量的监听任务里面使用！！！