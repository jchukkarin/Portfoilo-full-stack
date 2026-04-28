<template>
  <section id="about" class="about">
    <div class="container">
      <!-- LEFT: IMAGE -->
      <div class="left">
        <div class="image-wrapper">
          <img src="/ME02.jpg" alt="profile" />
        </div>
      </div>

      <!-- RIGHT: CONTENT -->
      <div class="right">
        <span class="badge">About me</span>

        <h1>Curious about me? Here you have it :</h1>

        <p>
          I am a 4th-year Software Engineering student at the University of Phayao with a strong
          foundation in full stack development. I have experience building web applications from
          frontend interfaces to backend systems, focusing on creating responsive, user-friendly,
          and scalable solutions.
        </p>

        <p>
          Currently, I am developing my skills in modern web technologies, including frontend and
          backend frameworks, API development, and database management. I enjoy solving problems
          through code and turning ideas into functional applications.
        </p>

        <p>
          I am also familiar with deployment processes using tools like Docker and CI/CD, allowing
          me to understand the full lifecycle of application development from development to
          production. I am seeking an internship opportunity from May to September to gain hands-on
          experience and grow as a Full Stack Developer.
        </p>
      </div>
    </div>
  </section>
</template>

<style scoped>
.about {
  padding: 100px 20px;
  background: var(--bg);
}

.about .container {
  display: grid;
  grid-template-columns: 1fr 1.5fr;
  gap: 80px;
  align-items: center;
  text-align: left;
  padding: 0;
}

.about .right {
  width: 70%;
  max-width: 800px;
  margin-left: auto;
}

/* LEFT */
.image-wrapper {
  position: relative;
}

.image-wrapper img {
  width: 100%;
  border-radius: 10px;
  position: relative;
  z-index: 2;
}

/* background effect */
.image-wrapper::before {
  content: '';
  position: absolute;
  top: 20px;
  left: -20px;
  width: 100%;
  height: 100%;
  background: #e5e7eb;
  z-index: 1;
  border-radius: 10px;
}

/* RIGHT */
.badge {
  background: var(--card);
  padding: 5px 10px;
  border-radius: 20px;
  font-size: 14px;
  font-weight: 600;
}

.about h1 {
  margin: 15px 0 16px 0;
  font-size: 32px;
  font-weight: 700;
  line-height: 1.2;
  letter-spacing: -1px;
}

.about p {
  margin-bottom: 24px;
  color: var(--subtext);
  line-height: 1.8;
  font-size: 18px;
  max-width: 600px;
}

/* RESPONSIVE */
@media (max-width: 768px) {
  .about {
    padding: 50px 20px;
  }

  .about .container {
    grid-template-columns: 1fr;
    gap: 40px;
    text-align: center;
  }

  .about h1 {
    font-size: 28px;
    text-align: center;
  }

  .about p {
    text-align: left;
    margin: 0 auto 24px;
    max-width: 100%;
  }

  .image-wrapper::before {
    display: none;
  }
}
</style>
