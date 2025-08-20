<script>
  import WebAppCard from './lib/WebAppCard.svelte';
  
  // 샘플 웹앱 데이터
  let webApps = [
    {
      id: 1,
      name: "Spotify",
      description: "음악 스트리밍 서비스로 전 세계의 다양한 음악을 즐길 수 있습니다.",
      image: "https://images.unsplash.com/photo-1614613535308-eb5fbd3d2c17?w=400&h=200&fit=crop",
      url: "https://open.spotify.com",
      tags: ["음악", "스트리밍", "엔터테인먼트"]
    },
    {
      id: 2,
      name: "Netflix",
      description: "영화와 TV 시리즈를 스트리밍할 수 있는 글로벌 플랫폼입니다.",
      image: "https://images.unsplash.com/photo-1574267432553-4b4628081c31?w=400&h=200&fit=crop",
      url: "https://www.netflix.com",
      tags: ["영화", "TV", "스트리밍"]
    },
    {
      id: 3,
      name: "Notion",
      description: "노트 작성, 프로젝트 관리, 협업을 위한 올인원 워크스페이스입니다.",
      image: "https://images.unsplash.com/photo-1551288049-bebda4e38f71?w=400&h=200&fit=crop",
      url: "https://www.notion.so",
      tags: ["생산성", "협업", "노트"]
    },
    {
      id: 4,
      name: "Figma",
      description: "디자인과 프로토타이핑을 위한 협업 디자인 도구입니다.",
      image: "https://images.unsplash.com/photo-1561070791-2526d30994b5?w=400&h=200&fit=crop",
      url: "https://www.figma.com",
      tags: ["디자인", "UI/UX", "협업"]
    },
    {
      id: 5,
      name: "Slack",
      description: "팀 커뮤니케이션과 협업을 위한 메시징 플랫폼입니다.",
      image: "https://images.unsplash.com/photo-1611224923853-80b023f02d71?w=400&h=200&fit=crop",
      url: "https://slack.com",
      tags: ["커뮤니케이션", "협업", "비즈니스"]
    },
    {
      id: 6,
      name: "Discord",
      description: "게이머와 커뮤니티를 위한 음성 및 텍스트 채팅 플랫폼입니다.",
      image: "https://images.unsplash.com/photo-1614680376408-81e91ffe3db7?w=400&h=200&fit=crop",
      url: "https://discord.com",
      tags: ["게임", "커뮤니티", "음성채팅"]
    }
  ];

  let searchTerm = '';
  let filteredApps = webApps;

  // 검색 기능
  $: {
    if (searchTerm.trim() === '') {
      filteredApps = webApps;
    } else {
      filteredApps = webApps.filter(app => 
        app.name.toLowerCase().includes(searchTerm.toLowerCase()) ||
        app.description.toLowerCase().includes(searchTerm.toLowerCase()) ||
        app.tags.some(tag => tag.toLowerCase().includes(searchTerm.toLowerCase()))
      );
    }
  }
</script>

<main>
  <div class="container">
    <header class="header">
      <h1 class="title">웹앱 갤러리</h1>
      <p class="subtitle">다양한 웹 애플리케이션을 탐색해보세요</p>
      
      <div class="search-container">
        <div class="search-box">
          <svg class="search-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <circle cx="11" cy="11" r="8"/>
            <path d="m21 21-4.35-4.35"/>
          </svg>
          <input 
            type="text" 
            placeholder="앱 이름, 설명 또는 태그로 검색..." 
            bind:value={searchTerm}
            class="search-input"
          />
        </div>
      </div>
    </header>

    <div class="content">
      {#if filteredApps.length === 0}
        <div class="no-results">
          <svg class="no-results-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <circle cx="11" cy="11" r="8"/>
            <path d="m21 21-4.35-4.35"/>
          </svg>
          <h3>검색 결과가 없습니다</h3>
          <p>다른 키워드로 검색해보세요</p>
        </div>
      {:else}
        <div class="cards-grid">
          {#each filteredApps as app (app.id)}
            <WebAppCard {app} />
          {/each}
        </div>
      {/if}
    </div>
  </div>

  <footer class="footer">
    <div class="footer-container">
      <div class="footer-content">
        <div class="company-info">
          <h3 class="company-name">VibeCoding</h3>
          <p class="company-description">
            혁신적인 웹 개발 솔루션을 제공하는 기술 회사입니다. 
            사용자 경험을 최우선으로 하는 창의적인 웹 애플리케이션을 개발하여 
            디지털 세계를 더욱 풍요롭게 만들어갑니다.
          </p>
        </div>
        
        <div class="footer-links">
          <div class="link-section">
            <h4>서비스</h4>
            <ul>
              <li><a href="#">웹 개발</a></li>
              <li><a href="#">모바일 앱</a></li>
              <li><a href="#">UI/UX 디자인</a></li>
              <li><a href="#">클라우드 솔루션</a></li>
            </ul>
          </div>
          
          <div class="link-section">
            <h4>회사</h4>
            <ul>
              <li><a href="#">소개</a></li>
              <li><a href="#">팀</a></li>
              <li><a href="#">채용</a></li>
              <li><a href="#">뉴스</a></li>
            </ul>
          </div>
          
          <div class="link-section">
            <h4>지원</h4>
            <ul>
              <li><a href="#">고객센터</a></li>
              <li><a href="#">문의하기</a></li>
              <li><a href="#">FAQ</a></li>
              <li><a href="#">개발자 문서</a></li>
            </ul>
          </div>
        </div>
      </div>
      
      <div class="footer-bottom">
        <div class="footer-bottom-content">
          <p class="copyright">© 2024 VibeCoding. All rights reserved.</p>
          <div class="social-links">
            <a href="#" class="social-link">
              <svg viewBox="0 0 24 24" fill="currentColor">
                <path d="M24 4.557c-.883.392-1.832.656-2.828.775 1.017-.609 1.798-1.574 2.165-2.724-.951.564-2.005.974-3.127 1.195-.897-.957-2.178-1.555-3.594-1.555-3.179 0-5.515 2.966-4.797 6.045-4.091-.205-7.719-2.165-10.148-5.144-1.29 2.213-.669 5.108 1.523 6.574-.806-.026-1.566-.247-2.229-.616-.054 2.281 1.581 4.415 3.949 4.89-.693.188-1.452.232-2.224.084.626 1.956 2.444 3.379 4.6 3.419-2.07 1.623-4.678 2.348-7.29 2.04 2.179 1.397 4.768 2.212 7.548 2.212 9.142 0 14.307-7.721 13.995-14.646.962-.695 1.797-1.562 2.457-2.549z"/>
              </svg>
            </a>
            <a href="#" class="social-link">
              <svg viewBox="0 0 24 24" fill="currentColor">
                <path d="M22.46 6c-.77.35-1.6.58-2.46.69.88-.53 1.56-1.37 1.88-2.38-.83.5-1.75.85-2.72 1.05C18.37 4.5 17.26 4 16 4c-2.35 0-4.27 1.92-4.27 4.29 0 .34.04.67.11.98C8.28 9.09 5.11 7.38 3 4.79c-.37.63-.58 1.37-.58 2.15 0 1.49.75 2.81 1.91 3.56-.71 0-1.37-.2-1.95-.5v.03c0 2.08 1.48 3.82 3.44 4.21a4.22 4.22 0 0 1-1.93.07 4.28 4.28 0 0 0 4 2.98 8.521 8.521 0 0 1-5.33 1.84c-.34 0-.68-.02-1.02-.06C3.44 20.29 5.7 21 8.12 21 16 21 20.33 14.46 20.33 8.79c0-.19 0-.37-.01-.56.84-.6 1.56-1.36 2.14-2.23z"/>
              </svg>
            </a>
            <a href="#" class="social-link">
              <svg viewBox="0 0 24 24" fill="currentColor">
                <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>
              </svg>
            </a>
            <a href="#" class="social-link">
              <svg viewBox="0 0 24 24" fill="currentColor">
                <path d="M12.017 0C5.396 0 .029 5.367.029 11.987c0 5.079 3.158 9.417 7.618 11.174-.105-.949-.199-2.403.041-3.439.219-.937 1.406-5.957 1.406-5.957s-.359-.72-.359-1.781c0-1.663.967-2.911 2.168-2.911 1.024 0 1.518.769 1.518 1.688 0 1.029-.653 2.567-.992 3.992-.285 1.193.6 2.165 1.775 2.165 2.128 0 3.768-2.245 3.768-5.487 0-2.861-2.063-4.869-5.008-4.869-3.41 0-5.409 2.562-5.409 5.199 0 1.033.394 2.143.889 2.741.099.12.112.225.085.345-.09.375-.293 1.199-.334 1.363-.053.225-.172.271-.402.165-1.495-.69-2.433-2.878-2.433-4.646 0-3.776 2.748-7.252 7.92-7.252 4.158 0 7.392 2.967 7.392 6.923 0 4.135-2.607 7.462-6.233 7.462-1.214 0-2.357-.629-2.746-1.378l-.748 2.853c-.271 1.043-1.002 2.35-1.492 3.146C9.57 23.812 10.763 24.009 12.017 24.009c6.624 0 11.99-5.367 11.99-11.988C24.007 5.367 18.641.001 12.017.001z"/>
              </svg>
            </a>
          </div>
        </div>
      </div>
    </div>
  </footer>
</main>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  main {
    min-height: 100vh;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    padding: 20px;
    display: flex;
    flex-direction: column;
  }

  .container {
    max-width: 1200px;
    margin: 0 auto;
    flex: 1;
  }

  .header {
    text-align: center;
    margin-bottom: 40px;
    color: white;
  }

  .title {
    font-size: 3rem;
    font-weight: 700;
    margin-bottom: 8px;
    text-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .subtitle {
    font-size: 1.1rem;
    opacity: 0.9;
    margin-bottom: 32px;
  }

  .search-container {
    display: flex;
    justify-content: center;
    margin-bottom: 20px;
  }

  .search-box {
    position: relative;
    max-width: 500px;
    width: 100%;
  }

  .search-icon {
    position: absolute;
    left: 16px;
    top: 50%;
    transform: translateY(-50%);
    width: 20px;
    height: 20px;
    color: #666;
    z-index: 1;
  }

  .search-input {
    width: 100%;
    padding: 16px 16px 16px 48px;
    border: none;
    border-radius: 50px;
    font-size: 1rem;
    background: white;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
    transition: all 0.3s ease;
  }

  .search-input:focus {
    outline: none;
    box-shadow: 0 6px 30px rgba(0, 0, 0, 0.15);
    transform: translateY(-2px);
  }

  .search-input::placeholder {
    color: #999;
  }

  .content {
    background: rgba(255, 255, 255, 0.1);
    border-radius: 24px;
    padding: 40px;
    backdrop-filter: blur(10px);
    margin-bottom: 40px;
  }

  .cards-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 32px;
    max-width: 100%;
  }

  .no-results {
    text-align: center;
    color: white;
    padding: 60px 20px;
  }

  .no-results-icon {
    width: 64px;
    height: 64px;
    margin: 0 auto 20px;
    opacity: 0.5;
  }

  .no-results h3 {
    font-size: 1.5rem;
    margin-bottom: 8px;
  }

  .no-results p {
    opacity: 0.8;
  }

  /* Footer Styles */
  .footer {
    background: rgba(0, 0, 0, 0.2);
    backdrop-filter: blur(10px);
    border-top: 1px solid rgba(255, 255, 255, 0.1);
    margin-top: auto;
  }

  .footer-container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 40px 20px 20px;
  }

  .footer-content {
    display: grid;
    grid-template-columns: 1fr 2fr;
    gap: 60px;
    margin-bottom: 40px;
  }

  .company-info {
    color: white;
  }

  .company-name {
    font-size: 1.8rem;
    font-weight: 700;
    margin-bottom: 16px;
    background: linear-gradient(135deg, #fff, #e0e7ff);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .company-description {
    line-height: 1.6;
    opacity: 0.9;
    font-size: 0.95rem;
  }

  .footer-links {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 40px;
  }

  .link-section h4 {
    color: white;
    font-size: 1.1rem;
    font-weight: 600;
    margin-bottom: 16px;
  }

  .link-section ul {
    list-style: none;
  }

  .link-section li {
    margin-bottom: 8px;
  }

  .link-section a {
    color: rgba(255, 255, 255, 0.8);
    text-decoration: none;
    transition: color 0.3s ease;
    font-size: 0.9rem;
  }

  .link-section a:hover {
    color: white;
  }

  .footer-bottom {
    border-top: 1px solid rgba(255, 255, 255, 0.1);
    padding-top: 20px;
  }

  .footer-bottom-content {
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: 20px;
  }

  .copyright {
    color: rgba(255, 255, 255, 0.7);
    font-size: 0.9rem;
  }

  .social-links {
    display: flex;
    gap: 16px;
  }

  .social-link {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 40px;
    height: 40px;
    background: rgba(255, 255, 255, 0.1);
    border-radius: 50%;
    color: white;
    transition: all 0.3s ease;
  }

  .social-link:hover {
    background: rgba(255, 255, 255, 0.2);
    transform: translateY(-2px);
  }

  .social-link svg {
    width: 20px;
    height: 20px;
  }

  @media (max-width: 1024px) {
    .cards-grid {
      grid-template-columns: repeat(2, 1fr);
      gap: 24px;
    }
  }

  @media (max-width: 768px) {
    .title {
      font-size: 2rem;
    }
    
    .content {
      padding: 20px;
    }
    
    .cards-grid {
      grid-template-columns: repeat(2, 1fr);
      gap: 20px;
    }

    .footer-content {
      grid-template-columns: 1fr;
      gap: 40px;
    }

    .footer-links {
      grid-template-columns: repeat(2, 1fr);
      gap: 30px;
    }

    .footer-bottom-content {
      flex-direction: column;
      text-align: center;
    }
  }

  @media (max-width: 640px) {
    .cards-grid {
      grid-template-columns: 1fr;
      gap: 20px;
    }
  }

  @media (max-width: 480px) {
    .footer-links {
      grid-template-columns: 1fr;
    }
  }
</style>
