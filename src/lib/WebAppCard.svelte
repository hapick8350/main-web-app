<script>
  export let app;
</script>

<a href={app.url} target="_blank" rel="noopener noreferrer" class="card-link">
  <div class="card">
    <div class="card-image">
      <img src={app.image} alt={app.name} />
    </div>
    <div class="card-content">
      <h3 class="card-title">{app.name}</h3>
      <p class="card-description">{app.description}</p>
      <div class="card-tags">
        {#each app.tags as tag}
          <span class="tag">{tag}</span>
        {/each}
      </div>
    </div>
  </div>
</a>

<style>
  .card-link {
    text-decoration: none;
    color: inherit;
    display: block;
    max-width: 320px;
    width: 100%;
  }

  .card {
    background: white;
    border-radius: 16px;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
    overflow: hidden;
    transition: all 0.3s ease;
    cursor: pointer;
    width: 100%;
    justify-self: center;
  }

  .card:hover {
    transform: translateY(-8px);
    box-shadow: 0 12px 40px rgba(0, 0, 0, 0.15);
  }

  .card-image {
    width: 100%;
    height: 200px;
    overflow: hidden;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  }

  .card-image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.3s ease;
  }

  .card:hover .card-image img {
    transform: scale(1.05);
  }

  .card-content {
    padding: 20px;
  }

  .card-title {
    margin: 0 0 12px 0;
    font-size: 1.25rem;
    font-weight: 600;
    color: #1a1a1a;
    line-height: 1.3;
  }

  .card-description {
    margin: 0 0 16px 0;
    color: #666;
    line-height: 1.5;
    font-size: 0.9rem;
  }

  .card-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  .tag {
    background: #f0f4ff;
    color: #4a6cf7;
    padding: 4px 12px;
    border-radius: 20px;
    font-size: 0.8rem;
    font-weight: 500;
  }
</style>
