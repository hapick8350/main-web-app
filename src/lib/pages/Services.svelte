<script>
  import { onMount } from 'svelte';
  
  let currentService = 0;
  const services = [
    {
      title: "웹 개발",
      description: "현대적이고 반응형 웹 애플리케이션 개발",
      icon: "🌐",
      features: [
        "React, Vue, Svelte 기반 개발",
        "반응형 웹 디자인",
        "SEO 최적화",
        "성능 최적화",
        "보안 강화"
      ],
      color: "from-blue-500 to-purple-600"
    },
    {
      title: "모바일 앱",
      description: "iOS 및 Android 네이티브 앱 개발",
      icon: "📱",
      features: [
        "React Native 개발",
        "Flutter 크로스 플랫폼",
        "네이티브 iOS/Android",
        "앱 스토어 배포",
        "푸시 알림 시스템"
      ],
      color: "from-green-500 to-teal-600"
    },
    {
      title: "UI/UX 디자인",
      description: "사용자 중심의 직관적인 인터페이스 디자인",
      icon: "🎨",
      features: [
        "사용자 리서치",
        "와이어프레임 & 프로토타입",
        "인터랙션 디자인",
        "디자인 시스템 구축",
        "사용성 테스트"
      ],
      color: "from-pink-500 to-rose-600"
    },
    {
      title: "클라우드 솔루션",
      description: "확장 가능한 클라우드 인프라 구축",
      icon: "☁️",
      features: [
        "AWS, Azure, GCP 구축",
        "마이크로서비스 아키텍처",
        "DevOps 자동화",
        "모니터링 & 로깅",
        "보안 & 백업"
      ],
      color: "from-orange-500 to-red-600"
    }
  ];

  onMount(() => {
    const interval = setInterval(() => {
      currentService = (currentService + 1) % services.length;
    }, 5000);
    
    return () => clearInterval(interval);
  });
</script>

<div class="services-page">
  <div class="hero-section">
    <div class="hero-content">
      <h1 class="hero-title">서비스</h1>
      <p class="hero-subtitle">혁신적인 기술 솔루션으로 비즈니스의 디지털 전환을 지원합니다</p>
    </div>
  </div>

  <div class="services-grid">
    {#each services as service, index}
      <div class="service-card" class:active={currentService === index}>
        <div class="service-icon bg-gradient-to-r {service.color}">
          <span class="text-4xl">{service.icon}</span>
        </div>
        <h3 class="service-title">{service.title}</h3>
        <p class="service-description">{service.description}</p>
        <ul class="service-features">
          {#each service.features as feature}
            <li class="feature-item">
              <span class="feature-icon">✓</span>
              {feature}
            </li>
          {/each}
        </ul>
        <button class="service-button">
          자세히 보기
        </button>
      </div>
    {/each}
  </div>

  <div class="cta-section">
    <div class="cta-content">
      <h2>프로젝트를 시작해보세요</h2>
      <p>당신의 아이디어를 현실로 만들어드립니다</p>
      <button class="cta-button">무료 상담 신청</button>
    </div>
  </div>
</div>

<style>
  .services-page {
    min-height: 100vh;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  }

  .hero-section {
    padding: 80px 20px;
    text-align: center;
    color: white;
  }

  .hero-title {
    font-size: 3.5rem;
    font-weight: 700;
    margin-bottom: 16px;
    text-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .hero-subtitle {
    font-size: 1.2rem;
    opacity: 0.9;
    max-width: 600px;
    margin: 0 auto;
    line-height: 1.6;
  }

  .services-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 32px;
    padding: 40px 20px;
    max-width: 1200px;
    margin: 0 auto;
  }

  .service-card {
    background: white;
    border-radius: 20px;
    padding: 32px;
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
    transition: all 0.3s ease;
    transform: translateY(0);
  }

  .service-card:hover {
    transform: translateY(-8px);
    box-shadow: 0 16px 48px rgba(0, 0, 0, 0.15);
  }

  .service-card.active {
    transform: translateY(-8px);
    box-shadow: 0 16px 48px rgba(0, 0, 0, 0.15);
  }

  .service-icon {
    width: 80px;
    height: 80px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 24px;
    color: white;
  }

  .service-title {
    font-size: 1.5rem;
    font-weight: 600;
    margin-bottom: 12px;
    color: #1a1a1a;
  }

  .service-description {
    color: #666;
    margin-bottom: 24px;
    line-height: 1.6;
  }

  .service-features {
    list-style: none;
    margin-bottom: 24px;
  }

  .feature-item {
    display: flex;
    align-items: center;
    margin-bottom: 8px;
    color: #555;
    font-size: 0.9rem;
  }

  .feature-icon {
    color: #10b981;
    font-weight: bold;
    margin-right: 8px;
  }

  .service-button {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    border: none;
    padding: 12px 24px;
    border-radius: 25px;
    font-weight: 500;
    cursor: pointer;
    transition: all 0.3s ease;
    width: 100%;
  }

  .service-button:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 12px rgba(102, 126, 234, 0.4);
  }

  .cta-section {
    background: rgba(255, 255, 255, 0.1);
    backdrop-filter: blur(10px);
    padding: 60px 20px;
    text-align: center;
    color: white;
    margin-top: 40px;
  }

  .cta-content h2 {
    font-size: 2.5rem;
    font-weight: 700;
    margin-bottom: 16px;
  }

  .cta-content p {
    font-size: 1.1rem;
    margin-bottom: 32px;
    opacity: 0.9;
  }

  .cta-button {
    background: white;
    color: #667eea;
    border: none;
    padding: 16px 32px;
    border-radius: 30px;
    font-size: 1.1rem;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.3s ease;
  }

  .cta-button:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 24px rgba(255, 255, 255, 0.3);
  }

  @media (max-width: 768px) {
    .hero-title {
      font-size: 2.5rem;
    }
    
    .services-grid {
      grid-template-columns: 1fr;
      gap: 24px;
      padding: 20px;
    }
    
    .service-card {
      padding: 24px;
    }
  }
</style>
