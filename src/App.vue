<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const currentBannerIndex = ref(0);
const bannerImages = [
  "https://images.unsplash.com/photo-1566073771259-6a8506099945?w=1600&h=900&fit=crop",
  "https://images.unsplash.com/photo-1551882547-ff40c63fe5fa?w=1600&h=900&fit=crop",
  "https://images.unsplash.com/photo-1542314831-068cd1dbfeeb?w=1600&h=900&fit=crop",
  "https://images.unsplash.com/photo-1564501049412-61c2a3083791?w=1600&h=900&fit=crop",
];

let bannerInterval = null;

onMounted(() => {
  bannerInterval = setInterval(() => {
    currentBannerIndex.value =
      (currentBannerIndex.value + 1) % bannerImages.length;
  }, 5000);
});

onUnmounted(() => {
  if (bannerInterval) clearInterval(bannerInterval);
});

const features = [
  {
    icon: "⚡",
    title: "30 秒入住体验",
    description: "身份证 + 人脸核验，全流程自动化",
  },
  {
    icon: "🔄",
    title: "深度 PMS 中台",
    description: "对接主流 PMS，订单 / 房态自动同步",
  },
  {
    icon: "🔐",
    title: "智能物联控制",
    description: "自动开锁、自动取电、门牌联动",
  },
  {
    icon: "🤖",
    title: "AI 酒店助手",
    description: "自动处理入住、续住、退房等重复事务",
  },
];

const products = [
  {
    name: "自助入住系统",
    desc: "小程序 / 自助机",
    icon: "📱",
  },
  {
    name: "酒店中台",
    desc: "PMS 同步/风控/自动执行",
    icon: "⚙️",
  },
  {
    name: "智慧物联控制",
    desc: "门锁/取电/门牌",
    icon: "🏠",
  },
  {
    name: "AI 酒店助手",
    desc: "自动流程执行",
    icon: "💬",
  },
];

const cases = [
  {
    location: "长沙 · 80 间中型酒店",
    stats: ["自助入住率达 72%", "前台人力成本减少 40%"],
  },
  {
    location: "湘潭 · 130 间连锁酒店",
    stats: ["全流程无人工入住", "客诉率下降 35%"],
  },
];

const techStack = [
  ".NET 8 / C#",
  "Vue 3 / Uni-app",
  "Redis / RocketMQ / MySQL",
  "WPF 自助机框架",
  "阿里云 / 腾讯云",
];
</script>

<template>
  <div class="website">
    <!-- 导航栏 -->
    <nav class="navbar">
      <div class="container">
        <div class="logo">
          <span class="logo-icon">🏨</span>
          <span class="logo-text">澜序科技</span>
        </div>
        <div class="nav-links">
          <a href="#home">首页</a>
          <a href="#features">核心功能</a>
          <a href="#products">产品</a>
          <a href="#cases">案例</a>
          <a href="#about">关于我们</a>
          <a href="#contact">联系我们</a>
        </div>
      </div>
    </nav>

    <!-- Banner 轮播 -->
    <section id="home" class="banner">
      <div class="banner-slider">
        <div
          v-for="(image, index) in bannerImages"
          :key="index"
          class="banner-slide"
          :class="{ active: currentBannerIndex === index }"
          :style="{ backgroundImage: `url(${image})` }"
        ></div>
      </div>
      <div class="banner-overlay"></div>
      <div class="banner-content">
        <h1 class="banner-title">澜序科技</h1>
        <p class="banner-subtitle">AI × 物联 × 自动化</p>
        <p class="banner-desc">让酒店运营更轻、更快、更安全</p>
        <button class="cta-button">了解更多</button>
      </div>
      <div class="banner-indicators">
        <span
          v-for="(_, index) in bannerImages"
          :key="index"
          class="indicator"
          :class="{ active: currentBannerIndex === index }"
          @click="currentBannerIndex = index"
        ></span>
      </div>
    </section>

    <!-- 核心功能 -->
    <section id="features" class="features">
      <div class="container">
        <h2 class="section-title">核心功能</h2>
        <div class="features-grid">
          <div
            v-for="(feature, index) in features"
            :key="index"
            class="feature-card"
            :style="{ animationDelay: `${index * 0.1}s` }"
          >
            <div class="feature-icon">{{ feature.icon }}</div>
            <h3>{{ feature.title }}</h3>
            <p>{{ feature.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- 产品快速入口 -->
    <section id="products" class="products">
      <div class="container">
        <h2 class="section-title">产品快速入口</h2>
        <div class="products-grid">
          <div
            v-for="(product, index) in products"
            :key="index"
            class="product-card"
            :style="{ animationDelay: `${index * 0.1}s` }"
          >
            <div class="product-icon">{{ product.icon }}</div>
            <h3>{{ product.name }}</h3>
            <p>{{ product.desc }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- 客户案例 -->
    <section id="cases" class="cases">
      <div class="container">
        <h2 class="section-title">客户案例</h2>
        <div class="cases-grid">
          <div
            v-for="(caseItem, index) in cases"
            :key="index"
            class="case-card"
            :style="{ animationDelay: `${index * 0.2}s` }"
          >
            <h3>{{ caseItem.location }}</h3>
            <ul>
              <li v-for="(stat, i) in caseItem.stats" :key="i">
                <span class="checkmark">✓</span>
                {{ stat }}
              </li>
            </ul>
          </div>
        </div>
      </div>
    </section>

    <!-- 关于我们 -->
    <section id="about" class="about">
      <div class="container">
        <h2 class="section-title">关于我们</h2>
        <div class="about-content">
          <div class="about-intro">
            <p class="intro-text">
              澜序科技是一家专注于智慧酒店系统、AI
              酒店助手与物联网控制的技术公司。 团队来自酒店
              SaaS、一线互联网企业，拥有丰富的行业经验。
            </p>
          </div>
          <div class="about-sections">
            <div class="about-section">
              <h3>💻 我们的技术栈</h3>
              <ul class="tech-list">
                <li v-for="(tech, index) in techStack" :key="index">
                  <span class="tech-dot"></span>
                  {{ tech }}
                </li>
              </ul>
            </div>
            <div class="about-section">
              <h3>🎯 我们的使命</h3>
              <p class="mission-text">让酒店运营更轻松，让入住更便捷。</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- 联系我们 -->
    <section id="contact" class="contact">
      <div class="container">
        <h2 class="section-title">联系我们</h2>
        <div class="contact-grid">
          <div class="contact-item">
            <div class="contact-icon">🏢</div>
            <h4>公司名称</h4>
            <p>澜序科技</p>
          </div>
          <div class="contact-item">
            <div class="contact-icon">📍</div>
            <h4>公司地址</h4>
            <p>湖南长沙</p>
          </div>
          <div class="contact-item">
            <div class="contact-icon">💬</div>
            <h4>微信</h4>
            <p>xxxxxx</p>
          </div>
          <div class="contact-item">
            <div class="contact-icon">📞</div>
            <h4>联系电话</h4>
            <p>xxxxxx</p>
          </div>
          <div class="contact-item">
            <div class="contact-icon">✉️</div>
            <h4>电子邮箱</h4>
            <p>contact@xxxx.com</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <footer class="footer">
      <div class="container">
        <p>&copy; 2025 澜序科技. All rights reserved.</p>
        <p class="footer-slogan">
          AI × 物联 × 自动化，让酒店运营更轻、更快、更安全
        </p>
      </div>
    </footer>
  </div>
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.website {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "PingFang SC",
    "Hiragino Sans GB", "Microsoft YaHei", sans-serif;
  color: #333;
  overflow-x: hidden;
}

/* 导航栏 */
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(10px);
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  z-index: 1000;
  animation: slideDown 0.5s ease-out;
}

@keyframes slideDown {
  from {
    transform: translateY(-100%);
  }
  to {
    transform: translateY(0);
  }
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

.navbar .container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 20px;
}

.logo {
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 1.5rem;
  font-weight: bold;
  color: #2563eb;
}

.logo-icon {
  font-size: 2rem;
  animation: float 3s ease-in-out infinite;
}

@keyframes float {
  0%,
  100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-10px);
  }
}

.nav-links {
  display: flex;
  gap: 2rem;
}

.nav-links a {
  text-decoration: none;
  color: #333;
  font-weight: 500;
  transition: color 0.3s;
  position: relative;
}

.nav-links a::after {
  content: "";
  position: absolute;
  bottom: -5px;
  left: 0;
  width: 0;
  height: 2px;
  background: #2563eb;
  transition: width 0.3s;
}

.nav-links a:hover {
  color: #2563eb;
}

.nav-links a:hover::after {
  width: 100%;
}

/* Banner */
.banner {
  position: relative;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

.banner-slider {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.banner-slide {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-size: cover;
  background-position: center;
  opacity: 0;
  transition: opacity 1s ease-in-out;
}

.banner-slide.active {
  opacity: 1;
}

.banner-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(
    135deg,
    rgba(37, 99, 235, 0.8),
    rgba(139, 92, 246, 0.8)
  );
}

.banner-content {
  position: relative;
  z-index: 10;
  text-align: center;
  color: white;
  animation: fadeInUp 1s ease-out;
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.banner-title {
  font-size: 4rem;
  margin-bottom: 1rem;
  font-weight: bold;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
}

.banner-subtitle {
  font-size: 2rem;
  margin-bottom: 0.5rem;
  font-weight: 600;
}

.banner-desc {
  font-size: 1.5rem;
  margin-bottom: 2rem;
  opacity: 0.9;
}

.cta-button {
  padding: 15px 40px;
  font-size: 1.2rem;
  background: white;
  color: #2563eb;
  border: none;
  border-radius: 50px;
  cursor: pointer;
  font-weight: bold;
  transition: all 0.3s;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
}

.cta-button:hover {
  transform: translateY(-3px);
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.3);
}

.banner-indicators {
  position: absolute;
  bottom: 30px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  gap: 10px;
  z-index: 10;
}

.indicator {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.5);
  cursor: pointer;
  transition: all 0.3s;
}

.indicator.active {
  background: white;
  width: 30px;
  border-radius: 6px;
}

/* Section 通用样式 */
section {
  padding: 80px 0;
}

.section-title {
  font-size: 2.5rem;
  text-align: center;
  margin-bottom: 3rem;
  color: #1e293b;
  position: relative;
}

.section-title::after {
  content: "";
  position: absolute;
  bottom: -10px;
  left: 50%;
  transform: translateX(-50%);
  width: 80px;
  height: 4px;
  background: linear-gradient(90deg, #2563eb, #8b5cf6);
  border-radius: 2px;
}

/* 核心功能 */
.features {
  background: linear-gradient(180deg, #f8fafc 0%, #ffffff 100%);
}

.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
}

.feature-card {
  background: white;
  padding: 2rem;
  border-radius: 20px;
  text-align: center;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
  transition: all 0.3s;
  animation: fadeInUp 0.6s ease-out backwards;
}

.feature-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 8px 30px rgba(37, 99, 235, 0.15);
}

.feature-icon {
  font-size: 3rem;
  margin-bottom: 1rem;
  animation: bounce 2s ease-in-out infinite;
}

@keyframes bounce {
  0%,
  100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-10px);
  }
}

.feature-card h3 {
  font-size: 1.5rem;
  margin-bottom: 1rem;
  color: #2563eb;
}

.feature-card p {
  color: #64748b;
  line-height: 1.6;
}

/* 产品快速入口 */
.products-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
}

.product-card {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  padding: 2rem;
  border-radius: 20px;
  text-align: center;
  color: white;
  transition: all 0.3s;
  animation: fadeInUp 0.6s ease-out backwards;
  cursor: pointer;
}

.product-card:hover {
  transform: translateY(-10px) scale(1.02);
  box-shadow: 0 10px 40px rgba(102, 126, 234, 0.4);
}

.product-icon {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.product-card h3 {
  font-size: 1.3rem;
  margin-bottom: 0.5rem;
}

.product-card p {
  opacity: 0.9;
  font-size: 0.9rem;
}

/* 客户案例 */
.cases {
  background: linear-gradient(180deg, #f8fafc 0%, #ffffff 100%);
}

.cases-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
}

.case-card {
  background: white;
  padding: 2.5rem;
  border-radius: 20px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
  border-left: 4px solid #2563eb;
  transition: all 0.3s;
  animation: fadeInUp 0.6s ease-out backwards;
}

.case-card:hover {
  transform: translateX(10px);
  box-shadow: 0 8px 30px rgba(37, 99, 235, 0.15);
}

.case-card h3 {
  font-size: 1.5rem;
  color: #2563eb;
  margin-bottom: 1.5rem;
}

.case-card ul {
  list-style: none;
}

.case-card li {
  padding: 0.8rem 0;
  color: #475569;
  display: flex;
  align-items: center;
  gap: 10px;
}

.checkmark {
  color: #10b981;
  font-weight: bold;
  font-size: 1.2rem;
}

/* 关于我们 */
.about-content {
  max-width: 900px;
  margin: 0 auto;
}

.about-intro {
  text-align: center;
  margin-bottom: 3rem;
}

.intro-text {
  font-size: 1.2rem;
  line-height: 1.8;
  color: #475569;
}

.about-sections {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 3rem;
}

.about-section {
  background: linear-gradient(135deg, #f8fafc 0%, #e0e7ff 100%);
  padding: 2rem;
  border-radius: 20px;
}

.about-section h3 {
  font-size: 1.5rem;
  margin-bottom: 1.5rem;
  color: #1e293b;
}

.tech-list {
  list-style: none;
}

.tech-list li {
  padding: 0.8rem 0;
  color: #475569;
  display: flex;
  align-items: center;
  gap: 10px;
}

.tech-dot {
  width: 8px;
  height: 8px;
  background: #2563eb;
  border-radius: 50%;
}

.mission-text {
  font-size: 1.3rem;
  line-height: 1.8;
  color: #2563eb;
  font-weight: 600;
}

/* 联系我们 */
.contact {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
}

.contact .section-title {
  color: white;
}

.contact .section-title::after {
  background: white;
}

.contact-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 2rem;
}

.contact-item {
  text-align: center;
  padding: 1.5rem;
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  border-radius: 15px;
  transition: all 0.3s;
}

.contact-item:hover {
  background: rgba(255, 255, 255, 0.2);
  transform: translateY(-5px);
}

.contact-icon {
  font-size: 2.5rem;
  margin-bottom: 1rem;
}

.contact-item h4 {
  font-size: 1.1rem;
  margin-bottom: 0.5rem;
  opacity: 0.9;
}

.contact-item p {
  font-size: 1rem;
  font-weight: 500;
}

/* Footer */
.footer {
  background: #1e293b;
  color: white;
  padding: 2rem 0;
  text-align: center;
}

.footer p {
  margin: 0.5rem 0;
}

.footer-slogan {
  opacity: 0.7;
  font-size: 0.9rem;
}

/* 响应式设计 */
@media (max-width: 768px) {
  .nav-links {
    display: none;
  }

  .banner-title {
    font-size: 2.5rem;
  }

  .banner-subtitle {
    font-size: 1.5rem;
  }

  .banner-desc {
    font-size: 1.2rem;
  }

  .section-title {
    font-size: 2rem;
  }

  .features-grid,
  .products-grid,
  .cases-grid,
  .contact-grid {
    grid-template-columns: 1fr;
  }
}
</style>
