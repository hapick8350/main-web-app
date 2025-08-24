<script>
  import { onMount } from 'svelte';
  
  let currentSection = 'contact';
  let activeFaq = null;
  
  let faqs = [
    {
      question: "프로젝트 견적은 어떻게 받을 수 있나요?",
      answer: "프로젝트 견적은 문의하기 페이지를 통해 상담 신청을 해주시면, 24시간 내에 전문 상담사가 연락드립니다. 프로젝트의 규모와 요구사항에 따라 맞춤형 견적을 제공해드립니다."
    },
    {
      question: "개발 기간은 얼마나 걸리나요?",
      answer: "프로젝트의 복잡도와 규모에 따라 다르지만, 일반적으로 소규모 웹사이트는 2-4주, 중간 규모 프로젝트는 1-3개월, 대규모 프로젝트는 3-6개월 정도 소요됩니다."
    },
    {
      question: "유지보수 서비스는 제공하나요?",
      answer: "네, 모든 프로젝트에 대해 유지보수 서비스를 제공합니다. 기본 1년 무료 유지보수와 함께, 이후 연간 유지보수 계약을 통해 안정적인 서비스를 보장합니다."
    },
    {
      question: "기술 스택은 어떤 것을 사용하나요?",
      answer: "프론트엔드는 React, Vue.js, Svelte, 백엔드는 Node.js, Python, Java, 데이터베이스는 PostgreSQL, MongoDB, Redis 등을 사용합니다. 프로젝트 요구사항에 맞는 최적의 기술 스택을 제안해드립니다."
    },
    {
      question: "해외 프로젝트도 진행하나요?",
      answer: "네, 해외 프로젝트도 진행합니다. 원격 협업 도구를 활용하여 전 세계 어디서든 효율적인 프로젝트 진행이 가능합니다."
    }
  ];

  let contactForm = {
    name: '',
    email: '',
    company: '',
    subject: '',
    message: ''
  };

  function setSection(section) {
    currentSection = section;
  }

  function toggleFaq(index) {
    activeFaq = activeFaq === index ? null : index;
  }

  function handleSubmit() {
    // 폼 제출 로직
    console.log('Contact form submitted:', contactForm);
    alert('문의가 성공적으로 전송되었습니다. 빠른 시일 내에 연락드리겠습니다.');
  }
</script>

<div class="support-page">
  <div class="hero-section">
    <div class="hero-content">
      <h1 class="hero-title">지원</h1>
      <p class="hero-subtitle">고객님의 성공을 위한 전문적인 지원 서비스를 제공합니다</p>
    </div>
  </div>

  <div class="navigation-tabs">
    <button 
      class="nav-tab" 
      class:active={currentSection === 'contact'}
      on:click={() => setSection('contact')}
    >
      문의하기
    </button>
    <button 
      class="nav-tab" 
      class:active={currentSection === 'faq'}
      on:click={() => setSection('faq')}
    >
      FAQ
    </button>
    <button 
      class="nav-tab" 
      class:active={currentSection === 'center'}
      on:click={() => setSection('center')}
    >
      고객센터
    </button>
    <button 
      class="nav-tab" 
      class:active={currentSection === 'docs'}
      on:click={() => setSection('docs')}
    >
      개발자 문서
    </button>
  </div>

  <div class="content-section">
    {#if currentSection === 'contact'}
      <div class="contact-section">
        <div class="contact-grid">
          <div class="contact-info">
            <h2>문의하기</h2>
            <p class="contact-description">
              프로젝트 문의, 기술 상담, 견적 요청 등 무엇이든 편하게 문의해주세요. 
              전문 상담사가 빠른 시일 내에 답변드리겠습니다.
            </p>
            
            <div class="contact-methods">
              <div class="contact-method">
                <div class="method-icon">📧</div>
                <div class="method-info">
                  <h4>이메일</h4>
                  <p>contact@firsti.com</p>
                </div>
              </div>
              
              <div class="contact-method">
                <div class="method-icon">📞</div>
                <div class="method-info">
                  <h4>전화</h4>
                  <p>02-1234-5678</p>
                </div>
              </div>
              
              <div class="contact-method">
                <div class="method-icon">💬</div>
                <div class="method-info">
                  <h4>카카오톡</h4>
                  <p>@Firsti</p>
                </div>
              </div>
            </div>
          </div>
          
          <div class="contact-form-container">
            <form class="contact-form" on:submit|preventDefault={handleSubmit}>
              <div class="form-group">
                <label for="name">이름 *</label>
                <input 
                  type="text" 
                  id="name" 
                  bind:value={contactForm.name} 
                  required 
                  placeholder="이름을 입력해주세요"
                />
              </div>
              
              <div class="form-group">
                <label for="email">이메일 *</label>
                <input 
                  type="email" 
                  id="email" 
                  bind:value={contactForm.email} 
                  required 
                  placeholder="이메일을 입력해주세요"
                />
              </div>
              
              <div class="form-group">
                <label for="company">회사명</label>
                <input 
                  type="text" 
                  id="company" 
                  bind:value={contactForm.company} 
                  placeholder="회사명을 입력해주세요"
                />
              </div>
              
              <div class="form-group">
                <label for="subject">제목 *</label>
                <input 
                  type="text" 
                  id="subject" 
                  bind:value={contactForm.subject} 
                  required 
                  placeholder="문의 제목을 입력해주세요"
                />
              </div>
              
              <div class="form-group">
                <label for="message">메시지 *</label>
                <textarea 
                  id="message" 
                  bind:value={contactForm.message} 
                  required 
                  placeholder="문의 내용을 자세히 입력해주세요"
                  rows="6"
                ></textarea>
              </div>
              
              <button type="submit" class="submit-button">
                문의하기
              </button>
            </form>
          </div>
        </div>
      </div>
    {:else if currentSection === 'faq'}
      <div class="faq-section">
        <h2>자주 묻는 질문</h2>
        <p class="faq-intro">고객님들이 자주 문의하시는 질문들을 모았습니다.</p>
        
        <div class="faq-list">
          {#each faqs as faq, index}
            <div class="faq-item" class:active={activeFaq === index}>
              <button class="faq-question" on:click={() => toggleFaq(index)}>
                <span>{faq.question}</span>
                <span class="faq-icon">{activeFaq === index ? '−' : '+'}</span>
              </button>
              <div class="faq-answer">
                <p>{faq.answer}</p>
              </div>
            </div>
          {/each}
        </div>
      </div>
    {:else if currentSection === 'center'}
      <div class="center-section">
        <h2>고객센터</h2>
        
        <div class="center-grid">
          <div class="center-card">
            <div class="center-icon">🛠️</div>
            <h3>기술 지원</h3>
            <p>개발 과정에서 발생하는 기술적 문제를 전문적으로 해결해드립니다.</p>
            <ul>
              <li>버그 수정</li>
              <li>성능 최적화</li>
              <li>보안 강화</li>
              <li>호환성 문제 해결</li>
            </ul>
            <button class="center-button">기술 지원 요청</button>
          </div>
          
          <div class="center-card">
            <div class="center-icon">📊</div>
            <h3>운영 지원</h3>
            <p>서비스 운영과 관련된 모든 문제를 해결해드립니다.</p>
            <ul>
              <li>서버 모니터링</li>
              <li>백업 및 복구</li>
              <li>업데이트 관리</li>
              <li>트래픽 관리</li>
            </ul>
            <button class="center-button">운영 지원 요청</button>
          </div>
          
          <div class="center-card">
            <div class="center-icon">📚</div>
            <h3>교육 지원</h3>
            <p>시스템 사용법과 관리 방법을 교육해드립니다.</p>
            <ul>
              <li>관리자 교육</li>
              <li>사용자 매뉴얼</li>
              <li>온라인 튜토리얼</li>
              <li>기술 워크샵</li>
            </ul>
            <button class="center-button">교육 지원 요청</button>
          </div>
        </div>
        
        <div class="support-stats">
          <div class="stat-item">
            <div class="stat-number">24/7</div>
            <div class="stat-label">지원 가능</div>
          </div>
          <div class="stat-item">
            <div class="stat-number">2시간</div>
            <div class="stat-label">평균 응답 시간</div>
          </div>
          <div class="stat-item">
            <div class="stat-number">98%</div>
            <div class="stat-label">고객 만족도</div>
          </div>
        </div>
      </div>
    {:else if currentSection === 'docs'}
      <div class="docs-section">
        <h2>개발자 문서</h2>
        <p class="docs-intro">API 사용법과 개발 가이드를 확인하세요.</p>
        
        <div class="docs-grid">
          <div class="doc-card">
            <div class="doc-icon">📖</div>
            <h3>API 문서</h3>
            <p>REST API와 GraphQL API의 상세한 사용법을 제공합니다.</p>
            <div class="doc-features">
              <span class="doc-feature">REST API</span>
              <span class="doc-feature">GraphQL</span>
              <span class="doc-feature">Webhooks</span>
            </div>
            <button class="doc-button">API 문서 보기</button>
          </div>
          
          <div class="doc-card">
            <div class="doc-icon">🔧</div>
            <h3>SDK & 라이브러리</h3>
            <p>다양한 프로그래밍 언어용 SDK와 라이브러리를 제공합니다.</p>
            <div class="doc-features">
              <span class="doc-feature">JavaScript</span>
              <span class="doc-feature">Python</span>
              <span class="doc-feature">Java</span>
            </div>
            <button class="doc-button">SDK 다운로드</button>
          </div>
          
          <div class="doc-card">
            <div class="doc-icon">🎯</div>
            <h3>시작 가이드</h3>
            <p>첫 번째 프로젝트를 빠르게 시작할 수 있는 가이드를 제공합니다.</p>
            <div class="doc-features">
              <span class="doc-feature">Quick Start</span>
              <span class="doc-feature">Tutorials</span>
              <span class="doc-feature">Examples</span>
            </div>
            <button class="doc-button">시작하기</button>
          </div>
          
          <div class="doc-card">
            <div class="doc-icon">💡</div>
            <h3>모범 사례</h3>
            <p>성공적인 프로젝트를 위한 모범 사례와 팁을 제공합니다.</p>
            <div class="doc-features">
              <span class="doc-feature">Architecture</span>
              <span class="doc-feature">Security</span>
              <span class="doc-feature">Performance</span>
            </div>
            <button class="doc-button">모범 사례 보기</button>
          </div>
        </div>
      </div>
    {/if}
  </div>
</div>

<style>
  .support-page {
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

  .contact-section h2,
  .faq-section h2,
  .center-section h2,
  .docs-section h2 {
    font-size: 2.5rem;
    font-weight: 700;
    margin-bottom: 24px;
    color: white;
    text-align: center;
  }

  .contact-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 40px;
    align-items: start;
  }

  .contact-info {
    background: white;
    border-radius: 20px;
    padding: 32px;
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
  }

  .contact-description {
    font-size: 1.1rem;
    line-height: 1.6;
    color: #666;
    margin-bottom: 32px;
  }

  .contact-methods {
    display: flex;
    flex-direction: column;
    gap: 20px;
  }

  .contact-method {
    display: flex;
    align-items: center;
    gap: 16px;
  }

  .method-icon {
    font-size: 2rem;
    width: 60px;
    height: 60px;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
  }

  .method-info h4 {
    font-size: 1.1rem;
    font-weight: 600;
    margin-bottom: 4px;
    color: #1a1a1a;
  }

  .method-info p {
    color: #666;
    font-size: 0.9rem;
  }

  .contact-form-container {
    background: white;
    border-radius: 20px;
    padding: 32px;
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
  }

  .contact-form {
    display: flex;
    flex-direction: column;
    gap: 20px;
  }

  .form-group {
    display: flex;
    flex-direction: column;
    gap: 8px;
  }

  .form-group label {
    font-weight: 600;
    color: #1a1a1a;
  }

  .form-group input,
  .form-group textarea {
    padding: 12px 16px;
    border: 2px solid #e5e7eb;
    border-radius: 12px;
    font-size: 1rem;
    transition: all 0.3s ease;
  }

  .form-group input:focus,
  .form-group textarea:focus {
    outline: none;
    border-color: #667eea;
    box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
  }

  .submit-button {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    border: none;
    padding: 16px 32px;
    border-radius: 12px;
    font-size: 1.1rem;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.3s ease;
  }

  .submit-button:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 24px rgba(102, 126, 234, 0.4);
  }

  .faq-intro {
    text-align: center;
    color: white;
    font-size: 1.1rem;
    margin-bottom: 40px;
    opacity: 0.9;
  }

  .faq-list {
    max-width: 800px;
    margin: 0 auto;
  }

  .faq-item {
    background: white;
    border-radius: 16px;
    margin-bottom: 16px;
    overflow: hidden;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
  }

  .faq-question {
    width: 100%;
    padding: 24px;
    background: none;
    border: none;
    text-align: left;
    font-size: 1.1rem;
    font-weight: 600;
    color: #1a1a1a;
    cursor: pointer;
    display: flex;
    justify-content: space-between;
    align-items: center;
    transition: all 0.3s ease;
  }

  .faq-question:hover {
    background: #f8fafc;
  }

  .faq-icon {
    font-size: 1.5rem;
    font-weight: bold;
    color: #667eea;
  }

  .faq-answer {
    max-height: 0;
    overflow: hidden;
    transition: max-height 0.3s ease;
  }

  .faq-item.active .faq-answer {
    max-height: 200px;
  }

  .faq-answer p {
    padding: 0 24px 24px;
    color: #666;
    line-height: 1.6;
  }

  .center-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 24px;
    margin-bottom: 40px;
  }

  .center-card {
    background: white;
    border-radius: 20px;
    padding: 32px;
    text-align: center;
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
    transition: all 0.3s ease;
  }

  .center-card:hover {
    transform: translateY(-8px);
    box-shadow: 0 16px 48px rgba(0, 0, 0, 0.15);
  }

  .center-icon {
    font-size: 3rem;
    margin-bottom: 20px;
  }

  .center-card h3 {
    font-size: 1.5rem;
    font-weight: 600;
    margin-bottom: 16px;
    color: #1a1a1a;
  }

  .center-card p {
    color: #666;
    line-height: 1.6;
    margin-bottom: 20px;
  }

  .center-card ul {
    list-style: none;
    margin-bottom: 24px;
    text-align: left;
  }

  .center-card li {
    color: #666;
    margin-bottom: 8px;
    padding-left: 20px;
    position: relative;
  }

  .center-card li::before {
    content: "✓";
    color: #10b981;
    position: absolute;
    left: 0;
    font-weight: bold;
  }

  .center-button {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    border: none;
    padding: 12px 24px;
    border-radius: 25px;
    font-weight: 500;
    cursor: pointer;
    transition: all 0.3s ease;
  }

  .center-button:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 12px rgba(102, 126, 234, 0.4);
  }

  .support-stats {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 24px;
    margin-top: 40px;
  }

  .stat-item {
    background: white;
    border-radius: 16px;
    padding: 24px;
    text-align: center;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
  }

  .stat-number {
    font-size: 2rem;
    font-weight: 700;
    color: #667eea;
    margin-bottom: 8px;
  }

  .stat-label {
    color: #666;
    font-size: 0.9rem;
  }

  .docs-intro {
    text-align: center;
    color: white;
    font-size: 1.1rem;
    margin-bottom: 40px;
    opacity: 0.9;
  }

  .docs-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 24px;
  }

  .doc-card {
    background: white;
    border-radius: 20px;
    padding: 32px;
    text-align: center;
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
    transition: all 0.3s ease;
  }

  .doc-card:hover {
    transform: translateY(-8px);
    box-shadow: 0 16px 48px rgba(0, 0, 0, 0.15);
  }

  .doc-icon {
    font-size: 3rem;
    margin-bottom: 20px;
  }

  .doc-card h3 {
    font-size: 1.3rem;
    font-weight: 600;
    margin-bottom: 16px;
    color: #1a1a1a;
  }

  .doc-card p {
    color: #666;
    line-height: 1.6;
    margin-bottom: 20px;
  }

  .doc-features {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    justify-content: center;
    margin-bottom: 24px;
  }

  .doc-feature {
    background: #f0f4ff;
    color: #4a6cf7;
    padding: 4px 12px;
    border-radius: 20px;
    font-size: 0.8rem;
    font-weight: 500;
  }

  .doc-button {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    border: none;
    padding: 12px 24px;
    border-radius: 25px;
    font-weight: 500;
    cursor: pointer;
    transition: all 0.3s ease;
  }

  .doc-button:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 12px rgba(102, 126, 234, 0.4);
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
    
    .contact-grid {
      grid-template-columns: 1fr;
      gap: 24px;
    }
    
    .center-grid,
    .docs-grid {
      grid-template-columns: 1fr;
    }
    
    .support-stats {
      grid-template-columns: repeat(2, 1fr);
    }
  }
</style>
