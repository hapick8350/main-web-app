<script>
  import { onMount } from 'svelte';
  
  let currentSection = 'about';
  let teamMembers = [
    {
      name: "김민수",
      position: "CEO & Founder",
      image: "https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?w=200&h=200&fit=crop&crop=face",
      description: "10년 이상의 웹 개발 경험을 바탕으로 혁신적인 솔루션을 제공합니다.",
      skills: ["전략 기획", "기술 리더십", "비즈니스 개발"]
    },
    {
      name: "이지은",
      position: "CTO",
      image: "https://images.unsplash.com/photo-1494790108755-2616b612b786?w=200&h=200&fit=crop&crop=face",
      description: "최신 기술 트렌드를 파악하고 기술적 혁신을 주도합니다.",
      skills: ["아키텍처 설계", "DevOps", "클라우드 인프라"]
    },
    {
      name: "박준호",
      position: "Lead Designer",
      image: "https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?w=200&h=200&fit=crop&crop=face",
      description: "사용자 중심의 직관적인 디자인을 창조합니다.",
      skills: ["UI/UX 디자인", "프로토타이핑", "디자인 시스템"]
    },
    {
      name: "최수진",
      position: "Senior Developer",
      image: "https://images.unsplash.com/photo-1438761681033-6461ffad8d80?w=200&h=200&fit=crop&crop=face",
      description: "고품질 코드와 최적화된 성능을 보장합니다.",
      skills: ["React", "Node.js", "데이터베이스"]
    }
  ];

  let news = [
    {
      date: "2024.01.15",
      title: "새로운 AI 기반 웹 개발 도구 출시",
      excerpt: "개발자 생산성을 크게 향상시키는 AI 도구를 출시했습니다.",
      category: "기술"
    },
    {
      date: "2024.01.10",
      title: "대형 기업과의 파트너십 체결",
      excerpt: "글로벌 기업과의 전략적 파트너십을 통해 서비스 영역을 확장합니다.",
      category: "비즈니스"
    },
    {
      date: "2024.01.05",
      title: "2024년 기술 트렌드 리포트 발표",
      excerpt: "올해 주목해야 할 웹 개발 트렌드를 분석한 리포트를 발표했습니다.",
      category: "리서치"
    }
  ];

  let jobOpenings = [
    {
      title: "Senior Frontend Developer",
      department: "개발팀",
      type: "정규직",
      location: "서울",
      requirements: ["React/Vue.js 3년+", "TypeScript", "성능 최적화 경험"]
    },
    {
      title: "UI/UX Designer",
      department: "디자인팀",
      type: "정규직",
      location: "서울",
      requirements: ["Figma/Adobe XD", "사용자 리서치", "프로토타이핑"]
    },
    {
      title: "DevOps Engineer",
      department: "인프라팀",
      type: "정규직",
      location: "서울",
      requirements: ["AWS/Azure", "Docker/Kubernetes", "CI/CD"]
    }
  ];

  function setSection(section) {
    currentSection = section;
  }
</script>

<div class="company-page">
  <div class="hero-section">
    <div class="hero-content">
      <h1 class="hero-title">회사</h1>
      <p class="hero-subtitle">혁신적인 기술로 더 나은 미래를 만들어갑니다</p>
    </div>
  </div>

  <div class="navigation-tabs">
    <button 
      class="nav-tab" 
      class:active={currentSection === 'about'}
      on:click={() => setSection('about')}
    >
      소개
    </button>
    <button 
      class="nav-tab" 
      class:active={currentSection === 'team'}
      on:click={() => setSection('team')}
    >
      팀
    </button>
    <button 
      class="nav-tab" 
      class:active={currentSection === 'careers'}
      on:click={() => setSection('careers')}
    >
      채용
    </button>
    <button 
      class="nav-tab" 
      class:active={currentSection === 'news'}
      on:click={() => setSection('news')}
    >
      뉴스
    </button>
  </div>

  <div class="content-section">
    {#if currentSection === 'about'}
      <div class="about-section">
        <div class="about-content">
          <h2>Firsti 소개</h2>
          <p class="about-description">
            Firsti는 혁신적인 웹 개발 솔루션을 제공하는 기술 회사입니다. 
            우리는 사용자 경험을 최우선으로 하는 창의적인 웹 애플리케이션을 개발하여 
            디지털 세계를 더욱 풍요롭게 만들어갑니다.
          </p>
          
          <div class="stats-grid">
            <div class="stat-item">
              <div class="stat-number">50+</div>
              <div class="stat-label">완료 프로젝트</div>
            </div>
            <div class="stat-item">
              <div class="stat-number">30+</div>
              <div class="stat-label">만족한 고객</div>
            </div>
            <div class="stat-item">
              <div class="stat-number">5년+</div>
              <div class="stat-label">업계 경험</div>
            </div>
            <div class="stat-item">
              <div class="stat-number">24/7</div>
              <div class="stat-label">고객 지원</div>
            </div>
          </div>

          <div class="values-section">
            <h3>우리의 가치</h3>
            <div class="values-grid">
              <div class="value-item">
                <div class="value-icon">🎯</div>
                <h4>혁신</h4>
                <p>최신 기술을 활용한 혁신적인 솔루션 제공</p>
              </div>
              <div class="value-item">
                <div class="value-icon">🤝</div>
                <h4>협업</h4>
                <p>고객과의 긴밀한 협업을 통한 최적의 결과</p>
              </div>
              <div class="value-item">
                <div class="value-icon">💎</div>
                <h4>품질</h4>
                <p>최고 품질의 코드와 서비스 제공</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    {:else if currentSection === 'team'}
      <div class="team-section">
        <h2>우리 팀</h2>
        <div class="team-grid">
          {#each teamMembers as member}
            <div class="team-card">
              <div class="member-image">
                <img src={member.image} alt={member.name} />
              </div>
              <div class="member-info">
                <h3 class="member-name">{member.name}</h3>
                <p class="member-position">{member.position}</p>
                <p class="member-description">{member.description}</p>
                <div class="member-skills">
                  {#each member.skills as skill}
                    <span class="skill-tag">{skill}</span>
                  {/each}
                </div>
              </div>
            </div>
          {/each}
        </div>
      </div>
    {:else if currentSection === 'careers'}
      <div class="careers-section">
        <h2>채용 정보</h2>
        <p class="careers-intro">함께 성장할 열정적인 인재를 찾고 있습니다.</p>
        
        <div class="jobs-grid">
          {#each jobOpenings as job}
            <div class="job-card">
              <h3 class="job-title">{job.title}</h3>
              <div class="job-meta">
                <span class="job-department">{job.department}</span>
                <span class="job-type">{job.type}</span>
                <span class="job-location">{job.location}</span>
              </div>
              <div class="job-requirements">
                <h4>요구사항:</h4>
                <ul>
                  {#each job.requirements as req}
                    <li>{req}</li>
                  {/each}
                </ul>
              </div>
              <button class="apply-button">지원하기</button>
            </div>
          {/each}
        </div>
      </div>
    {:else if currentSection === 'news'}
      <div class="news-section">
        <h2>뉴스 & 업데이트</h2>
        
        <div class="news-grid">
          {#each news as article}
            <div class="news-card">
              <div class="news-meta">
                <span class="news-date">{article.date}</span>
                <span class="news-category">{article.category}</span>
              </div>
              <h3 class="news-title">{article.title}</h3>
              <p class="news-excerpt">{article.excerpt}</p>
              <button class="read-more-button">자세히 보기</button>
            </div>
          {/each}
        </div>
      </div>
    {/if}
  </div>
</div>

<style>
  .company-page {
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

  .navigation-tabs {
    display: flex;
    justify-content: center;
    gap: 8px;
    padding: 20px;
    background: rgba(255, 255, 255, 0.1);
    backdrop-filter: blur(10px);
  }

  .nav-tab {
    background: rgba(255, 255, 255, 0.1);
    color: white;
    border: none;
    padding: 12px 24px;
    border-radius: 25px;
    font-weight: 500;
    cursor: pointer;
    transition: all 0.3s ease;
  }

  .nav-tab:hover {
    background: rgba(255, 255, 255, 0.2);
  }

  .nav-tab.active {
    background: white;
    color: #667eea;
  }

  .content-section {
    max-width: 1200px;
    margin: 0 auto;
    padding: 40px 20px;
  }

  .about-section {
    background: white;
    border-radius: 20px;
    padding: 40px;
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
  }

  .about-section h2 {
    font-size: 2.5rem;
    font-weight: 700;
    margin-bottom: 24px;
    color: #1a1a1a;
  }

  .about-description {
    font-size: 1.1rem;
    line-height: 1.8;
    color: #666;
    margin-bottom: 40px;
  }

  .stats-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 24px;
    margin-bottom: 40px;
  }

  .stat-item {
    text-align: center;
    padding: 24px;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    border-radius: 16px;
    color: white;
  }

  .stat-number {
    font-size: 2.5rem;
    font-weight: 700;
    margin-bottom: 8px;
  }

  .stat-label {
    font-size: 0.9rem;
    opacity: 0.9;
  }

  .values-section h3 {
    font-size: 2rem;
    font-weight: 600;
    margin-bottom: 24px;
    color: #1a1a1a;
  }

  .values-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 24px;
  }

  .value-item {
    text-align: center;
    padding: 24px;
    background: #f8fafc;
    border-radius: 16px;
  }

  .value-icon {
    font-size: 3rem;
    margin-bottom: 16px;
  }

  .value-item h4 {
    font-size: 1.3rem;
    font-weight: 600;
    margin-bottom: 12px;
    color: #1a1a1a;
  }

  .value-item p {
    color: #666;
    line-height: 1.6;
  }

  .team-section h2,
  .careers-section h2,
  .news-section h2 {
    font-size: 2.5rem;
    font-weight: 700;
    margin-bottom: 24px;
    color: white;
    text-align: center;
  }

  .team-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 32px;
  }

  .team-card {
    background: white;
    border-radius: 20px;
    padding: 32px;
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
    transition: all 0.3s ease;
  }

  .team-card:hover {
    transform: translateY(-8px);
    box-shadow: 0 16px 48px rgba(0, 0, 0, 0.15);
  }

  .member-image {
    width: 120px;
    height: 120px;
    border-radius: 50%;
    overflow: hidden;
    margin: 0 auto 24px;
  }

  .member-image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  .member-name {
    font-size: 1.5rem;
    font-weight: 600;
    margin-bottom: 8px;
    color: #1a1a1a;
    text-align: center;
  }

  .member-position {
    font-size: 1rem;
    color: #667eea;
    margin-bottom: 16px;
    text-align: center;
    font-weight: 500;
  }

  .member-description {
    color: #666;
    line-height: 1.6;
    margin-bottom: 20px;
    text-align: center;
  }

  .member-skills {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    justify-content: center;
  }

  .skill-tag {
    background: #f0f4ff;
    color: #4a6cf7;
    padding: 4px 12px;
    border-radius: 20px;
    font-size: 0.8rem;
    font-weight: 500;
  }

  .careers-intro {
    text-align: center;
    color: white;
    font-size: 1.1rem;
    margin-bottom: 40px;
    opacity: 0.9;
  }

  .jobs-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
    gap: 24px;
  }

  .job-card {
    background: white;
    border-radius: 16px;
    padding: 24px;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
  }

  .job-title {
    font-size: 1.3rem;
    font-weight: 600;
    margin-bottom: 12px;
    color: #1a1a1a;
  }

  .job-meta {
    display: flex;
    gap: 12px;
    margin-bottom: 16px;
  }

  .job-department,
  .job-type,
  .job-location {
    background: #f0f4ff;
    color: #4a6cf7;
    padding: 4px 12px;
    border-radius: 20px;
    font-size: 0.8rem;
    font-weight: 500;
  }

  .job-requirements h4 {
    font-size: 1rem;
    font-weight: 600;
    margin-bottom: 8px;
    color: #1a1a1a;
  }

  .job-requirements ul {
    list-style: none;
    margin-bottom: 20px;
  }

  .job-requirements li {
    color: #666;
    margin-bottom: 4px;
    padding-left: 16px;
    position: relative;
  }

  .job-requirements li::before {
    content: "•";
    color: #4a6cf7;
    position: absolute;
    left: 0;
  }

  .apply-button {
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

  .apply-button:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 12px rgba(102, 126, 234, 0.4);
  }

  .news-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 24px;
  }

  .news-card {
    background: white;
    border-radius: 16px;
    padding: 24px;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
    transition: all 0.3s ease;
  }

  .news-card:hover {
    transform: translateY(-4px);
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.15);
  }

  .news-meta {
    display: flex;
    gap: 12px;
    margin-bottom: 12px;
  }

  .news-date {
    color: #666;
    font-size: 0.9rem;
  }

  .news-category {
    background: #f0f4ff;
    color: #4a6cf7;
    padding: 2px 8px;
    border-radius: 12px;
    font-size: 0.8rem;
    font-weight: 500;
  }

  .news-title {
    font-size: 1.2rem;
    font-weight: 600;
    margin-bottom: 12px;
    color: #1a1a1a;
    line-height: 1.4;
  }

  .news-excerpt {
    color: #666;
    line-height: 1.6;
    margin-bottom: 16px;
  }

  .read-more-button {
    background: transparent;
    color: #4a6cf7;
    border: 2px solid #4a6cf7;
    padding: 8px 16px;
    border-radius: 20px;
    font-weight: 500;
    cursor: pointer;
    transition: all 0.3s ease;
  }

  .read-more-button:hover {
    background: #4a6cf7;
    color: white;
  }

  @media (max-width: 768px) {
    .hero-title {
      font-size: 2.5rem;
    }
    
    .navigation-tabs {
      flex-wrap: wrap;
    }
    
    .content-section {
      padding: 20px;
    }
    
    .about-section {
      padding: 24px;
    }
    
    .stats-grid {
      grid-template-columns: repeat(2, 1fr);
    }
    
    .team-grid,
    .jobs-grid,
    .news-grid {
      grid-template-columns: 1fr;
    }
  }
</style>
