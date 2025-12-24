# Lusion.co 网站复刻实现指南

## 项目概述

本指南将帮助你使用 Vite + React + GSAP + Lenis + Three.js + WebGL 技术栈，在 VS Code 中一步步实现 Lusion.co 风格的网站。

## 第一步：创建项目并安装依赖

### 1.1 初始化 Vite + React 项目

在终端中执行以下命令：

```bash
# 创建项目
npm create vite@latest lusion-clone -- --template react

# 进入项目目录
cd lusion-clone

# 安装基础依赖
npm install
```

### 1.2 安装所需的库

```bash
# 安装动画和滚动库
npm install gsap @studio-freight/lenis

# 安装 Three.js 相关
npm install three @react-three/fiber @react-three/drei

# 安装其他工具库
npm install react-router-dom
```

## 第二步：项目结构设置

### 2.1 创建文件夹结构

```
lusion-clone/
├── src/
│   ├── components/
│   │   ├── Header.jsx
│   │   ├── Loader.jsx
│   │   ├── Hero.jsx
│   │   ├── About.jsx
│   │   ├── FeaturedWork.jsx
│   │   ├── ProjectCard.jsx
│   │   ├── Footer.jsx
│   │   └── Canvas3D.jsx
│   ├── hooks/
│   │   └── useLenis.js
│   ├── styles/
│   │   └── global.css
│   ├── utils/
│   │   └── animations.js
│   ├── App.jsx
│   └── main.jsx
```

## 第三步：核心组件实现

### 3.1 全局样式 (src/styles/global.css)

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

:root {
  --color-bg: #000000;
  --color-text: #ffffff;
  --color-accent: #00ff00;
  --font-primary: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
}

html {
  scroll-behavior: auto;
}

body {
  font-family: var(--font-primary);
  background-color: var(--color-bg);
  color: var(--color-text);
  overflow-x: hidden;
}

html.lenis {
  height: auto;
}

.lenis.lenis-smooth {
  scroll-behavior: auto;
}

.lenis.lenis-smooth [data-lenis-prevent] {
  overscroll-behavior: contain;
}

.lenis.lenis-stopped {
  overflow: hidden;
}

.lenis.lenis-scrolling iframe {
  pointer-events: none;
}
```

### 3.2 Lenis 平滑滚动 Hook (src/hooks/useLenis.js)

```javascript
import { useEffect } from 'react';
import Lenis from '@studio-freight/lenis';

export const useLenis = () => {
  useEffect(() => {
    const lenis = new Lenis({
      duration: 1.2,
      easing: (t) => Math.min(1, 1.001 - Math.pow(2, -10 * t)),
      orientation: 'vertical',
      smoothWheel: true,
      wheelMultiplier: 1,
      smoothTouch: false,
      touchMultiplier: 2,
    });

    function raf(time) {
      lenis.raf(time);
      requestAnimationFrame(raf);
    }

    requestAnimationFrame(raf);

    return () => {
      lenis.destroy();
    };
  }, []);
};
```

### 3.3 加载动画组件 (src/components/Loader.jsx)

```javascript
import { useEffect, useRef, useState } from 'react';
import { gsap } from 'gsap';
import './Loader.css';

const Loader = ({ onLoadComplete }) => {
  const [progress, setProgress] = useState(0);
  const loaderRef = useRef(null);
  const progressBarRef = useRef(null);
  const counterRef = useRef(null);

  useEffect(() => {
    // 模拟加载进度
    const duration = 3; // 3秒加载时间
    const startTime = Date.now();

    const updateProgress = () => {
      const elapsed = (Date.now() - startTime) / 1000;
      const newProgress = Math.min((elapsed / duration) * 100, 100);
      setProgress(newProgress);

      if (newProgress < 100) {
        requestAnimationFrame(updateProgress);
      } else {
        // 加载完成，执行退出动画
        gsap.to(loaderRef.current, {
          opacity: 0,
          duration: 0.8,
          ease: 'power2.inOut',
          onComplete: () => {
            onLoadComplete();
          },
        });
      }
    };

    requestAnimationFrame(updateProgress);

    // 进度条动画
    gsap.to(progressBarRef.current, {
      scaleX: 1,
      duration: duration,
      ease: 'power2.inOut',
    });
  }, [onLoadComplete]);

  return (
    <div ref={loaderRef} className="loader">
      <div className="loader-progress">
        <div className="progress-bar-container">
          <div ref={progressBarRef} className="progress-bar"></div>
        </div>
      </div>
      <div ref={counterRef} className="loader-counter">
        {Math.floor(progress).toString().padStart(3, '0')}
      </div>
    </div>
  );
};

export default Loader;
```

### 3.4 加载动画样式 (src/components/Loader.css)

```css
.loader {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-color: #000;
  z-index: 9999;
  display: flex;
  align-items: center;
  justify-content: center;
}

.loader-progress {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 200px;
  height: 4px;
}

.progress-bar-container {
  width: 100%;
  height: 100%;
  background-color: #333;
  overflow: hidden;
}

.progress-bar {
  width: 100%;
  height: 100%;
  background-color: #fff;
  transform-origin: left;
  transform: scaleX(0);
}

.loader-counter {
  position: absolute;
  bottom: 10%;
  left: 5%;
  font-size: 120px;
  font-weight: 700;
  color: #fff;
  letter-spacing: -0.05em;
}
```

### 3.5 导航栏组件 (src/components/Header.jsx)

```javascript
import { useEffect, useRef } from 'react';
import { gsap } from 'gsap';
import './Header.css';

const Header = () => {
  const headerRef = useRef(null);

  useEffect(() => {
    gsap.fromTo(
      headerRef.current,
      { y: -100, opacity: 0 },
      { y: 0, opacity: 1, duration: 1, delay: 3.5, ease: 'power3.out' }
    );
  }, []);

  return (
    <header ref={headerRef} className="header">
      <div className="header-logo">
        <a href="/">LUSION</a>
      </div>
      <div className="header-right">
        <button className="header-btn sound-btn">
          <span className="btn-icon">🔊</span>
        </button>
        <button className="header-btn talk-btn">LET'S TALK</button>
        <button className="header-btn menu-btn">MENU</button>
      </div>
    </header>
  );
};

export default Header;
```

### 3.6 导航栏样式 (src/components/Header.css)

```css
.header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  padding: 30px 50px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  z-index: 1000;
  mix-blend-mode: difference;
}

.header-logo a {
  font-size: 24px;
  font-weight: 700;
  color: #fff;
  text-decoration: none;
  letter-spacing: 0.1em;
}

.header-right {
  display: flex;
  gap: 20px;
  align-items: center;
}

.header-btn {
  background: transparent;
  border: 1px solid #fff;
  color: #fff;
  padding: 12px 24px;
  font-size: 12px;
  font-weight: 600;
  letter-spacing: 0.1em;
  cursor: pointer;
  transition: all 0.3s ease;
}

.header-btn:hover {
  background: #fff;
  color: #000;
}

.sound-btn {
  padding: 12px;
  border-radius: 50%;
}

.btn-icon {
  font-size: 16px;
}
```

### 3.7 Hero 主视觉区域 (src/components/Hero.jsx)

```javascript
import { useEffect, useRef } from 'react';
import { gsap } from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';
import './Hero.css';

gsap.registerPlugin(ScrollTrigger);

const Hero = () => {
  const heroRef = useRef(null);
  const titleRef = useRef(null);
  const subtitleRef = useRef(null);

  useEffect(() => {
    const tl = gsap.timeline({ delay: 4 });

    tl.fromTo(
      titleRef.current,
      { y: 100, opacity: 0 },
      { y: 0, opacity: 1, duration: 1.2, ease: 'power3.out' }
    ).fromTo(
      subtitleRef.current,
      { y: 50, opacity: 0 },
      { y: 0, opacity: 1, duration: 1, ease: 'power3.out' },
      '-=0.6'
    );

    // 滚动视差效果
    gsap.to(heroRef.current, {
      scrollTrigger: {
        trigger: heroRef.current,
        start: 'top top',
        end: 'bottom top',
        scrub: true,
      },
      y: 200,
      opacity: 0.5,
    });
  }, []);

  return (
    <section ref={heroRef} className="hero">
      <div className="hero-content">
        <h1 ref={titleRef} className="hero-title">
          We help brands create
          <br />
          digital experiences that
          <br />
          connect with their audience
        </h1>
        <p ref={subtitleRef} className="hero-subtitle">
          scroll to explore
        </p>
      </div>
    </section>
  );
};

export default Hero;
```

### 3.8 Hero 样式 (src/components/Hero.css)

```css
.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  padding: 0 50px;
}

.hero-content {
  text-align: center;
  max-width: 1200px;
}

.hero-title {
  font-size: clamp(40px, 6vw, 80px);
  font-weight: 700;
  line-height: 1.2;
  margin-bottom: 40px;
  letter-spacing: -0.02em;
}

.hero-subtitle {
  font-size: 14px;
  font-weight: 400;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  opacity: 0.6;
}
```

### 3.9 Three.js 3D 背景 (src/components/Canvas3D.jsx)

```javascript
import { useRef, useEffect } from 'react';
import * as THREE from 'three';
import './Canvas3D.css';

const Canvas3D = () => {
  const canvasRef = useRef(null);

  useEffect(() => {
    if (!canvasRef.current) return;

    // 场景设置
    const scene = new THREE.Scene();
    const camera = new THREE.PerspectiveCamera(
      75,
      window.innerWidth / window.innerHeight,
      0.1,
      1000
    );
    const renderer = new THREE.WebGLRenderer({
      canvas: canvasRef.current,
      alpha: true,
      antialias: true,
    });

    renderer.setSize(window.innerWidth, window.innerHeight);
    renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));

    // 创建粒子系统
    const particlesGeometry = new THREE.BufferGeometry();
    const particlesCount = 1000;
    const posArray = new Float32Array(particlesCount * 3);

    for (let i = 0; i < particlesCount * 3; i++) {
      posArray[i] = (Math.random() - 0.5) * 10;
    }

    particlesGeometry.setAttribute(
      'position',
      new THREE.BufferAttribute(posArray, 3)
    );

    const particlesMaterial = new THREE.PointsMaterial({
      size: 0.02,
      color: 0xffffff,
      transparent: true,
      opacity: 0.8,
    });

    const particlesMesh = new THREE.Points(
      particlesGeometry,
      particlesMaterial
    );
    scene.add(particlesMesh);

    camera.position.z = 3;

    // 鼠标交互
    let mouseX = 0;
    let mouseY = 0;

    const handleMouseMove = (event) => {
      mouseX = (event.clientX / window.innerWidth) * 2 - 1;
      mouseY = -(event.clientY / window.innerHeight) * 2 + 1;
    };

    window.addEventListener('mousemove', handleMouseMove);

    // 动画循环
    const animate = () => {
      requestAnimationFrame(animate);

      particlesMesh.rotation.y += 0.001;
      particlesMesh.rotation.x = mouseY * 0.1;
      particlesMesh.rotation.y += mouseX * 0.01;

      renderer.render(scene, camera);
    };

    animate();

    // 响应式处理
    const handleResize = () => {
      camera.aspect = window.innerWidth / window.innerHeight;
      camera.updateProjectionMatrix();
      renderer.setSize(window.innerWidth, window.innerHeight);
    };

    window.addEventListener('resize', handleResize);

    return () => {
      window.removeEventListener('mousemove', handleMouseMove);
      window.removeEventListener('resize', handleResize);
      renderer.dispose();
    };
  }, []);

  return <canvas ref={canvasRef} className="canvas-3d" />;
};

export default Canvas3D;
```

### 3.10 Canvas 样式 (src/components/Canvas3D.css)

```css
.canvas-3d {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -1;
  pointer-events: none;
}
```

### 3.11 项目卡片组件 (src/components/ProjectCard.jsx)

```javascript
import { useRef, useEffect } from 'react';
import { gsap } from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';
import './ProjectCard.css';

gsap.registerPlugin(ScrollTrigger);

const ProjectCard = ({ title, tags, index }) => {
  const cardRef = useRef(null);

  useEffect(() => {
    gsap.fromTo(
      cardRef.current,
      { y: 100, opacity: 0 },
      {
        y: 0,
        opacity: 1,
        duration: 1,
        scrollTrigger: {
          trigger: cardRef.current,
          start: 'top 80%',
          end: 'top 50%',
          scrub: 1,
        },
      }
    );
  }, []);

  return (
    <div ref={cardRef} className="project-card">
      <div className="project-card-content">
        <div className="project-tags">
          {tags.map((tag, i) => (
            <span key={i} className="project-tag">
              {tag}
            </span>
          ))}
        </div>
        <h3 className="project-title">{title}</h3>
      </div>
    </div>
  );
};

export default ProjectCard;
```

### 3.12 项目卡片样式 (src/components/ProjectCard.css)

```css
.project-card {
  border: 1px solid rgba(255, 255, 255, 0.2);
  padding: 40px;
  transition: all 0.4s ease;
  cursor: pointer;
  min-height: 300px;
  display: flex;
  align-items: flex-end;
}

.project-card:hover {
  border-color: rgba(255, 255, 255, 0.6);
  transform: translateY(-10px);
}

.project-card-content {
  width: 100%;
}

.project-tags {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
  flex-wrap: wrap;
}

.project-tag {
  font-size: 11px;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  opacity: 0.6;
}

.project-title {
  font-size: 32px;
  font-weight: 700;
  letter-spacing: -0.02em;
}
```

### 3.13 作品展示区域 (src/components/FeaturedWork.jsx)

```javascript
import ProjectCard from './ProjectCard';
import './FeaturedWork.css';

const FeaturedWork = () => {
  const projects = [
    { title: 'Devin AI', tags: ['WEB', 'DESIGN', 'DEVELOPMENT', '3D'] },
    { title: 'Porsche: Drive', tags: ['CONCEPT', '3D ILLUSTRATION', 'MOGRAPH', 'VIDEO'] },
    { title: 'Synthetic Humans', tags: ['WEB', 'DESIGN', 'DEVELOPMENT', '3D'] },
    { title: 'Meta: Spatial Audio', tags: ['WEB', 'DESIGN', 'DEVELOPMENT', '3D'] },
    { title: 'Space-NFTM', tags: ['WEB', 'DESIGN', 'DEVELOPMENT', '3D', 'WEB3'] },
    { title: 'DD2024', tags: ['WEB', 'DESIGN', 'DEVELOPMENT', '3D'] },
  ];

  return (
    <section className="featured-work">
      <div className="featured-header">
        <h2 className="section-title">Featured Work</h2>
        <p className="section-subtitle">
          A selection of our most passionately crafted works with forward-thinking
          clients and friends over the years.
        </p>
      </div>
      <div className="projects-grid">
        {projects.map((project, index) => (
          <ProjectCard
            key={index}
            title={project.title}
            tags={project.tags}
            index={index}
          />
        ))}
      </div>
    </section>
  );
};

export default FeaturedWork;
```

### 3.14 作品展示样式 (src/components/FeaturedWork.css)

```css
.featured-work {
  padding: 150px 50px;
  max-width: 1600px;
  margin: 0 auto;
}

.featured-header {
  margin-bottom: 80px;
}

.section-title {
  font-size: clamp(40px, 5vw, 60px);
  font-weight: 700;
  margin-bottom: 20px;
  letter-spacing: -0.02em;
}

.section-subtitle {
  font-size: 18px;
  line-height: 1.6;
  opacity: 0.7;
  max-width: 600px;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
  gap: 30px;
}

@media (max-width: 768px) {
  .projects-grid {
    grid-template-columns: 1fr;
  }
}
```

### 3.15 主应用组件 (src/App.jsx)

```javascript
import { useState } from 'react';
import { useLenis } from './hooks/useLenis';
import Loader from './components/Loader';
import Header from './components/Header';
import Hero from './components/Hero';
import FeaturedWork from './components/FeaturedWork';
import Canvas3D from './components/Canvas3D';
import './styles/global.css';

function App() {
  const [isLoading, setIsLoading] = useState(true);

  useLenis();

  const handleLoadComplete = () => {
    setIsLoading(false);
  };

  return (
    <>
      {isLoading && <Loader onLoadComplete={handleLoadComplete} />}
      {!isLoading && (
        <>
          <Canvas3D />
          <Header />
          <main>
            <Hero />
            <FeaturedWork />
          </main>
        </>
      )}
    </>
  );
}

export default App;
```

## 第四步：运行项目

### 4.1 启动开发服务器

```bash
npm run dev
```

### 4.2 访问项目

打开浏览器访问 `http://localhost:5173`

## 第五步：优化和扩展

### 5.1 性能优化建议

1. **懒加载组件**：使用 React.lazy() 和 Suspense
2. **优化 Three.js**：减少粒子数量，使用 LOD（Level of Detail）
3. **图片优化**：使用 WebP 格式，添加懒加载
4. **代码分割**：使用动态 import

### 5.2 可以添加的功能

1. **更多 WebGL 效果**：使用 GLSL 着色器创建自定义效果
2. **页面过渡动画**：使用 GSAP 的 Flip 插件
3. **鼠标跟随效果**：自定义光标
4. **音效系统**：添加背景音乐和交互音效
5. **响应式设计**：完善移动端适配

### 5.3 WebGL 着色器示例

如果你想添加更高级的 WebGL 效果，可以创建自定义着色器：

```javascript
// src/shaders/vertexShader.glsl
varying vec2 vUv;

void main() {
  vUv = uv;
  gl_Position = projectionMatrix * modelViewMatrix * vec4(position, 1.0);
}
```

```javascript
// src/shaders/fragmentShader.glsl
uniform float uTime;
varying vec2 vUv;

void main() {
  vec2 uv = vUv;
  vec3 color = vec3(uv.x, uv.y, sin(uTime));
  gl_FragColor = vec4(color, 1.0);
}
```

## 常见问题解答

### Q1: GSAP 动画不流畅怎么办？
A: 确保使用 `will-change` CSS 属性，并使用 `transform` 和 `opacity` 而不是 `top`/`left`。

### Q2: Lenis 滚动卡顿？
A: 调整 `duration` 和 `easing` 参数，确保没有过多的 DOM 操作。

### Q3: Three.js 性能问题？
A: 减少粒子数量，使用 `InstancedMesh`，降低 `pixelRatio`。

### Q4: 如何调试 WebGL？
A: 使用 Chrome 的 Spector.js 扩展或 Three.js Inspector。

## 总结

这个项目涵盖了现代 Web 开发的多个关键技术：

- **Vite**：快速的开发构建工具
- **React**：组件化开发
- **GSAP**：强大的动画库
- **Lenis**：平滑滚动体验
- **Three.js**：3D 图形渲染
- **WebGL**：底层图形 API

按照这个指南，你可以创建一个具有专业视觉效果和流畅交互的现代网站。记得根据实际需求调整参数和效果！
