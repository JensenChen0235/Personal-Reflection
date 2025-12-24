# Jensen的积累日记
## 📅 12.16 前端之炫酷动效的来源，为什么那些炫酷网站很难有教学？
	因为他们用了这些技术栈！！！
Three.js：做 3D 主视觉。
GSAP：做动画时间线/转场 [https://lenis.darkroom.engineering/]
Lenis：做丝滑滚动 [https://gsap.com/]
Canvas：做 HUD/线条/粒子点缀
  所以作为一个半吊子写界面的人，要先打好react框架的基础，然后再能够灵活调用这些牛逼的库，最后要保持节约成本和提高转化的思想把东西实现出来。
  思考：最后作品要做出什么？或许做出一个炫酷网页并不是最终目的，但是要在AI时代找到自己的定位，我是一个能够做出高质量效果的全栈AI应用人才。
  
## 📅 12.19 我想做什么网站
#### 能够展示个人多维度能力网站
#### 1.个人信息：过往作品，日常思考
#### 2.动效能力：炫酷，交互感强，微交互充足
#### 3.建模能力：有自己做的或者扒拉下来的建模
#### 4.代码能力：能展示自己做agent
#### 5.解决问题能力：什么目标+什么场景+在此场景下的什么问题+怎么解决+怎么验证
#### 6.商业化思维：边际递减+机会成本+帕累托最优，打歼灭战

## 📅 12.19-12.22 临摹了苹果网站 [https://gsap-macbook-landing-vert.vercel.app/]  放在github并用vercel部署了
#### 技术栈：Vite+React
<img width="1718" height="2170" alt="image" src="https://github.com/user-attachments/assets/66bdd527-cf13-4b2c-96b5-dc3b98fa5425" />

0.用terminal里部署好环境，搭好框架 <br />
1.在App.jsx里写的是各个部分的框架 <br />
2.在/src/component文件夹里一个一个写每个部分的jsx文件 <br />
3.在/public文件夹里存资产 <br />
4.在public存资产 <br />
⚠️具体的语法还没有完全搞懂，视频间切换会产生loading的问题还没有解决(已解决，详见12.23 00:22的github更新)

## 📅 12.23 Mosh的React教程1-20
<img width="962" height="626" alt="image" src="https://github.com/user-attachments/assets/ebc37836-eb31-429f-a86c-2791cc24b2d3" /> <br/>
	return里面这里要用东西包着<br/>
<br/>

<img width="1122" height="640" alt="image" src="https://github.com/user-attachments/assets/d98ed710-9028-4525-a1f3-28819cd91fa5" />  <br/>
	这里的key是要说明我们应该给item一个key<br/>
	key 是 React 用来：<br/>
	•	区分列表里的每一项<br/>
	•	提高 diff & 更新性能<br/>
	•	防止渲染错乱<br/>

 
<img width="602" height="240" alt="image" src="https://github.com/user-attachments/assets/bea08626-cf00-4c8e-bd94-1564917834fe" /> <br/>
	className命名<br/>

<img width="1519" height="476" alt="image" src="https://github.com/user-attachments/assets/5f4744f4-027b-4a49-b935-379d010b89f5" /> <br/>
	语法: ? 前面如果是true输出？后面的，否则输出：后面的<br/>

<img width="804" height="42" alt="image" src="https://github.com/user-attachments/assets/5fdb58e8-a8d0-45ed-a550-6c0ee8388b18" />  <br/>
	语法：&&前面如果true输出&&后面的，否则不渲染在浏览器（看不到）<br/>

Prop VS State<br/>
Props 决定“你拿到什么”（从APP.tsx传到特定的组件的tsx），<br/>
State 决定“你现在处在什么状态”（组件里面自己的，比如选中了什么）。<br/>

<img width="1124" height="508" alt="image" src="https://github.com/user-attachments/assets/17745a63-874b-4633-9f43-dd27d8b8c840" /> <br/>
React Arrow Function Component Export<br/>

## 📅 12.23 Mosh的React教程20-
语法糖：让人更好吃，但不改变本质，降低人写代码的认知负担<br/>

<img width="118" height="120" alt="image" src="https://github.com/user-attachments/assets/c8695ace-b62e-4e62-a7b3-901b0339379a" /> <img width="122" height="118" alt="image" src="https://github.com/user-attachments/assets/e3edca1b-cdde-4088-8371-3b2ad48a07dd" /> <br/>

点赞的功能设计：<br/>
首先要分析点赞前状态（空心），点赞后状态（实心红色），把这两个在组件的tsx实现出来。<br/>
然后用一个useState来切换，对应（true or false），分别return实心和空心<br/>

为什么我写代码会举步维艰，从现在起得有抽象和宏观思维，不要沉浸在具体的语法，要先搭建解决的架构<br/>

asynchronously 异步：我先去干别的，好了再叫我











