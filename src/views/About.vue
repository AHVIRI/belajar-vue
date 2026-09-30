<template>
  <div class="about-page">
    <div class="about-header">
      <h1>About Gatherly</h1>
      <p>Building the future of event experiences, one community at a time.</p>
    </div>
    
    <div class="about-content">
      <div class="text-block">
        <h2>Our Mission</h2>
        <p>
          At Gatherly, our mission is to empower communities by providing a seamless, all-in-one platform for discovering, creating, and managing events. We believe that bringing people together fosters innovation, learning, and meaningful connections. Our goal is to remove the friction from event management so organizers can focus on what truly matters: delivering unforgettable experiences.
        </p>
      </div>
      
      <div class="text-block">
        <h2>Our Vision</h2>
        <p>
          We envision a world where anyone, anywhere, can easily find their tribe. Whether it's a small local tech meetup, a hands-on workshop, or a large-scale national competition, Gatherly aims to be the global standard for community-driven event infrastructure, bridging the gap between digital convenience and real-world interactions.
        </p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.about-page {
  animation: fadeIn 0.5s ease;
  max-width: 800px;
  margin: 0 auto;
}

.about-header {
  text-align: center;
  margin-bottom: 4rem;
  padding: 4rem 2rem;
  background: #fdfdfd;
  border-radius: 20px;
  border: 1px solid #f0f0f0;
}

.about-header h1 {
  font-size: 3rem;
  color: #1c1948;
  margin-bottom: 1rem;
}

.about-header p {
  font-size: 1.2rem;
  color: #666;
}

.about-content {
  display: flex;
  flex-direction: column;
  gap: 3rem;
  padding: 0 1rem;
}

.text-block h2 {
  color: #1c1948;
  font-size: 1.8rem;
  margin-bottom: 1.2rem;
  display: flex;
  align-items: center;
  gap: 1rem;
}

.text-block h2::before {
  content: "";
  display: block;
  width: 24px;
  height: 4px;
  background: #6644ff;
  border-radius: 2px;
}

.text-block p {
  color: #555;
  line-height: 1.8;
  font-size: 1.1rem;
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(10px); }
  to { opacity: 1; transform: translateY(0); }
}
</style>
