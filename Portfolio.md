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

## 📅 12.24 Mosh的React教程20-
语法糖：让人更好吃，但不改变本质，降低人写代码的认知负担<br/>

<img width="118" height="120" alt="image" src="https://github.com/user-attachments/assets/c8695ace-b62e-4e62-a7b3-901b0339379a" /> <img width="122" height="118" alt="image" src="https://github.com/user-attachments/assets/e3edca1b-cdde-4088-8371-3b2ad48a07dd" /> <br/>

点赞的功能设计：<br/>
首先要分析点赞前状态（空心），点赞后状态（实心红色），把这两个在组件的tsx实现出来。<br/>
然后用一个useState来切换，对应（true or false），分别return实心和空心<br/>

为什么我写代码会举步维艰，从现在起得有抽象和宏观思维，不要沉浸在具体的语法，要先搭建解决的架构<br/>

asynchronously 异步：我先去干别的，好了再叫我<br/>

## 📅 12.25 Lusion模拟+prompt格式刻意练习
<img width="694" height="486" alt="image" src="https://github.com/user-attachments/assets/5ae2c250-bf63-4487-8ce6-66eb69f192e5" /> <br/>
<img width="716" height="458" alt="image" src="https://github.com/user-attachments/assets/e44d7be5-2771-4eb9-b351-8972b9f6a216" /><br/>
<img width="1920" height="959" alt="image" src="https://github.com/user-attachments/assets/5330ac66-618d-4afc-b3d8-9acfff34f45d" /><br/>

这个方法真的天才，能轻松画出这样的曲线<br/>


Prompt的撰写
角色与目标：你是一名资深的前端架构师和网页3D建模渲染开发者。请帮我构建一个单文件（Single-File）的 React 应用，这是一个具有“拍照识别卡路里”功能的 Progressive Web App (PWA)。
技术栈：1.Framework: React (使用 Functional Components + Hooks)2.Styling: Tailwind CSS (追求现代、干净、移动端优先的 UI)3.Icons: Lucide-React4.AI Model: Gemini
核心功能：1.相机界面：主界面是一个全屏的取景框。底部有一个明显的圆形“快门/上传”按钮，支持 <input type="file" capture="environment" /> 调用后摄。2.实时 Gemini 分析：（1）核心逻辑：编写异步函数 analyzeFoodImage(base64Image, apiKey)。（2）SDK调用：初始化 GoogleGenerativeAI，获取 gemini-1.5-flash 模型。（3）Prompt设计：向 Gemini 发送图片和以下 Prompt："Analyze this image. Identify the food items. Return a JSON object with fields: foodName (string), calories (integer), protein (string, e.g., '20g'), carbs (string), fat (string), explanation (short sentence). Do not use Markdown formatting in the response, just raw JSON."（4）错误处理：处理 API 额度超限或网络错误，给予用户友好的 Toast 提示。3.结果展示卡片：（1）解析 Gemini 返回的 JSON 数据。（2）以精美的半透明磨砂玻璃（Glassmorphism）效果从底部弹出结果。（3）使用进度条可视化展示三大营养素占比。4.PWA 特性：（1）包含标准的 manifest.json 配置（作为注释块提供）。（2）界面必须适配移动端触摸操作（Touch-friendly）。5.设计美学：（1）配色方案：使用游戏科技配色，传达减脂、动感的感觉。（2）字体：无衬线字体，清晰易读。（3）应用的名字为“Jensen Cal”。6.功能需求：（1）加入历史记录功能，以天为记录单位记录每天的卡路里。（2）饮食目标为增肌、减肥或者保持体重，同时允许用户输入每日卡路里摄入的目标值。（3）每次记录的时候用户可以选择记录为早餐、午餐、晚餐还是加餐，记录可以修改。（4）用户点击历史记录卡片的时候，可以看到识别时候的详细信息。（5）每天的记录好早餐、午餐、晚餐之后（加餐非选项），出现“分析今日饮食”的按键，点击之后可以分析今日摄入卡路里的情况、改进的意见以及完成目标的情况（增肌、减肥、保持体重）。（6）用户可以点击右上角设置图标中的选择记录卡片按键进行全选删除。（7）饮食记录每一天的卡片格式帮我按照早餐、午餐和晚餐的格式排序。（8）如果识别之后不记录的话，照片记得帮我同时刷新去掉。（9）首次使用应用时，添加一个简短的用户引导流程，介绍核心功能：拍照识别、历史记录和饮食目标设置。7.输出要求：请生成一个完整的 .html 文件（包含 React 和 Babel 的 CDN 链接，以便单文件运行），代码需要有详细的注释，特别是 Gemini API 调用部分。

1.版本号：我已经按照你给我的代码，写到了我的VScode上，现在的版本需要标记版本1.0.
2.角色：你是一名非常擅长做创意网页，做出的网页获得过awwward的year of site的资深的前端架构师和网页3D建模渲染和动效开发者。
3.任务目标：
4.规则红线：
5.工作流程：
6.交付格式：
7.执行指令：


## 📅 12.26 做了一个SoundButton按钮
静音 <br/> 
<img width="66" height="64" alt="image" src="https://github.com/user-attachments/assets/2f9c7ee9-f07a-482b-8f19-deab293f3187" /> <br/> 
有动效播放 <br/> 
<img width="69" height="61" alt="image" src="https://github.com/user-attachments/assets/d96a06ed-9238-492b-ba1e-ae4a910e5d3f" /> <br/> 
Hover 从不同方位进去那个蓝色就从那个方位移入，然后Hover移出就从不同地方出去，会完全出去（解决了卡在边缘的问题） <br/> 
<img width="56" height="59" alt="image" src="https://github.com/user-attachments/assets/56840689-c2e8-4f3d-bb95-8fd256ac0c98" /> <br/> 
	
	<div className="labs-text-mask">
        <motion.span variants={{rest:{y:0}, hover:{y:"-100%"}}}>LABS</motion.span>
        <motion.span className="abs-top" variants={{rest:{y:"-100%"}, hover:{y:0}}}>LABS</motion.span>
    </div>

苹果的箭头→（ctrl+com+space调出来）在button是不一样的格式（要记得调样式），这个时候要改成div。<br/> 
	<div className="email-btn"> →</div>

<img width="960" height="925" alt="image" src="https://github.com/user-attachments/assets/05024687-e6a8-4654-8365-ab5cbbc2d445" /><br/> 

## 📅 12.27 做了AboutSection和Featured Work的内容
实现了仿照Lusion网站的3D的模型效果：<br/> 
	•	屏幕里有 30 个“工业积木”（其实是 3 根带孔圆柱互相贯穿 + 中间一个 RoundedBox 过渡块）。<br/> 
	•	它们都在一个 零重力物理世界里漂浮（Rapier Physics）。<br/> 
	•	它们会被一个“看不见的中心磁铁”往原点吸（向心力）。<br/> 
	•	同时又有一点“水中呼吸感”的随机漂移（drift）。<br/> 
	•	鼠标位置是一个“隐形推杆/推子”（kinematic collider），移动鼠标会推开物体。<br/> 
	•	点击（pointer down）会触发：<br/> 
	1.	切换配色（背景 + 彩色物体）<br/> 
	2.	从鼠标点击位置爆发一个“冲击波”，把附近物体震飞并甩着转（impulse + torque）<br/> 

再加上：<br/> 
	•	摄像机是自适应推拉的：窗口越宽越靠近，窗口越窄越拉远（AdaptiveCamera）。<br/> 
	•	灯光是“摄影棚 softbox”，环境光 + 三个 Lightformer。<br/> 
	•	后期做 AO（物体缝隙阴影）+ 色调映射（ToneMapping）。<br/> 

⚠️不会做Lusion这里的视频变大的动画。<br/> 

## 📅 12.28 反思了做的顺序
得先确定好布局，然后再去做效果，做效果的时候一点一点给AI说（之前做的顺序没有标准化，没有形成工作流）。<br/> 
prompt描述的时候得要有内容，比如说它改UI不能只说“所有要素”，要说颜色、圆角、字体这些能够被AI懂的，因为AI不会知道所有要素代表着什么。

## 📅 12.29 做了Footer和新建的放项目的页面。
使用了router来控制页面。<br/> 

	npm install react-router-dom
	
## 📅 12.30-31 做了Footer和新建的放项目的页面。
<img width="952" height="925" alt="image" src="https://github.com/user-attachments/assets/3a2e109d-9b06-4ae5-aa50-0090d2011ed4" /><br/> 
TRAE的footer底部设计可以参考，它是有点视差的感觉，然后鼠标滑有拖动的效果。

## 📅 1.1-1.3 改了音乐全局播放，做了各个按钮的音效

## 📅 1.4 react课
<img width="1086" height="695" alt="image" src="https://github.com/user-attachments/assets/4ac9277f-dd15-49ad-9c77-a067c413c027" />  
在使用usestate的时候，避免多余的变量，如果有多个变量可以把它弄成这样的组。
<img width="919" height="427" alt="image" src="https://github.com/user-attachments/assets/e58e4961-1338-4fba-8277-3d3f5b0d9129" />  
React 函数组件每一次渲染，都会“从头重新执行这个函数。  

## 📅 1.5 网站的project1优化
<img width="3444" height="1812" alt="image" src="https://github.com/user-attachments/assets/a5452a99-967c-48ea-9417-1101191190d0" />  
开始复刻苹果的这个点击切换，来展示项目的内容。

## 📅 1.6 节流和防抖
🧠 防抖（Debounce）= 电梯关门  
	•	你狂按关门键 ❌ 不关  
	•	等你 不按了  
	•	过 500ms 才真的关门  
  
👉 重点：等最后一次  
🧠 节流（Throttle）= 水龙头限流  
	•	你一直拧  
	•	水只会：  
	•	每 1 秒流一次  
	•	中间的操作直接忽略  
  
👉 重点：固定时间间隔  

## 📅 1.7 Project1布局
参考鲜时光  

## 📅 1.8-1.9 看Spec-coding
vibe coding更创意，复现难。
spec coding像是写了个PRD
<img width="3456" height="1926" alt="image" src="https://github.com/user-attachments/assets/fb44c36c-ddd5-4887-a2a1-cd82a7b1c687" />   
做了before和after以及数字的转动效果
## 📅 1.9 Project1黑色底的布局
<img width="3456" height="1926" alt="image" src="https://github.com/user-attachments/assets/7538bb31-b657-401f-8e25-fe895d0df54b" />  
搭好了motion lab的框架

## 📅 1.10 还是复刻不出效果
<img width="1900" height="772" alt="image" src="https://github.com/user-attachments/assets/99ed0fd1-3924-4804-bcb5-3239301dbdcf" />
要思考我放json文件还是要自己复刻一下。

## 📅 1.11 下滑到底部的About me
<img width="3456" height="1926" alt="image" src="https://github.com/user-attachments/assets/84b77d4d-8692-49a2-b8cc-fc0d6b4ac893" />  
做了点云的效果，做了About me的页面

## 📅 1.12-1.13 About的页面改良
<img width="3456" height="1926" alt="image" src="https://github.com/user-attachments/assets/1afb2138-723b-4bba-826e-337e5005f01f" />   
修改成这样了，左右布局，右边可以滚动经历，有点类似简历

## 📅 1.14 Logo背景
用luminance来判断背景是什么颜色的，如果深色就白色文字，反之亦然。
luminance = 0.2126 * R + 0.7152 * G + 0.0722 * B，WCAG 标准

## 📅 1.15 确定了Terabox要做的事站长中心的改版  
<img width="934" height="576" alt="image" src="https://github.com/user-attachments/assets/fff5e6ad-9ba1-4682-9e32-d072110f9bd5" />  
可以用上“鲜时光”的布局图
<img width="1140" height="1354" alt="image" src="https://github.com/user-attachments/assets/abb8cb9b-9086-47d9-ae08-48a24ad73a75" /> 

## 📅 1.16 写完Terabox每个部分要的内容  
要体现落地项目的优势  
WCAG guidelines：让残障用户、老年人、不同设备与环境下的用户，都能“看得见、听得懂、用得了、不会被卡死”。

## 📅 1.17 填充了前面的内容，包括植入了一个可播放的视频  
<img width="818" height="590" alt="image" src="https://github.com/user-attachments/assets/ebd81f4f-ffdb-46f3-8d60-9a376c8a8879" />

## 📅 1.18还有没调整的最后再调
<img width="866" height="364" alt="image" src="https://github.com/user-attachments/assets/41b3d120-9965-410f-bff6-d09b305c4503" />

## 📅 1.19部署上线了，暂无卡顿问题  
手机端的布局有很大问题

## 📅 1.20-21responsive design
做完了所有的此类设计，后续如果要继续设计，可以最后再调整布局。

## 📅 1.22-23terabox内容变junior，AI生成3d图

## 📅 1.24-25terabox做完persona

## 📅 1.24-26Layout Design之前

## 📅 1.27-1.30 休息

## 📅 1.31 修改了persona切换的效果

