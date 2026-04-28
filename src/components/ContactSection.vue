<script setup>
const copyText = (text) => {
  navigator.clipboard.writeText(text)
  alert('Copied: ' + text)
}
</script>
<template>
  <section id="contact" class="contact">
    <div class="container">
      <span class="tagline">Get in touch</span>

      <p class="desc">
        What’s next? Feel free to reach out to me if you're looking for a developer, have a query,
        or simply want to connect.
      </p>

      <!-- Email -->
      <div class="contact-item">
        <span class="icon"
          ><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24">
            <g
              fill="none"
              stroke="currentColor"
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
            >
              <path
                stroke-dasharray="66"
                d="M4 5h16c0.55 0 1 0.45 1 1v12c0 0.55 -0.45 1 -1 1h-16c-0.55 0 -1 -0.45 -1 -1v-12c0 -0.55 0.45 -1 1 -1Z"
              >
                <animate fill="freeze" attributeName="stroke-dashoffset" dur="0.6s" values="66;0" />
              </path>
              <path stroke-dasharray="24" stroke-dashoffset="24" d="M3 6.5l9 5.5l9 -5.5">
                <animate
                  fill="freeze"
                  attributeName="stroke-dashoffset"
                  begin="0.6s"
                  dur="0.3s"
                  to="0"
                />
              </path>
            </g></svg
        ></span>
        <span class="text">Chukkarin08@gmail.com</span>
        <button class="copy" @click="copyText('Chukkarin08@gmail.com')">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24">
            <g
              fill="none"
              stroke="currentColor"
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
            >
              <path
                d="M7 9.667A2.667 2.667 0 0 1 9.667 7h8.666A2.667 2.667 0 0 1 21 9.667v8.666A2.667 2.667 0 0 1 18.333 21H9.667A2.667 2.667 0 0 1 7 18.333z"
              />
              <path d="M4.012 16.737A2 2 0 0 1 3 15V5c0-1.1.9-2 2-2h10c.75 0 1.158.385 1.5 1" />
            </g>
          </svg>
        </button>
      </div>

      <!-- Phone -->
      <div class="contact-item">
        <span class="icon"
          ><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24">
            <path
              fill="none"
              stroke="currentColor"
              stroke-dasharray="62"
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M8 3c0.5 0 2.5 4.5 2.5 5c0 1 -1.5 2 -2 3c-0.5 1 0.5 2 1.5 3c0.39 0.39 2 2 3 1.5c1 -0.5 2 -2 3 -2c0.5 0 5 2 5 2.5c0 2 -1.5 3.5 -3 4c-1.5 0.5 -2.5 0.5 -4.5 0c-2 -0.5 -3.5 -1 -6 -3.5c-2.5 -2.5 -3 -4 -3.5 -6c-0.5 -2 -0.5 -3 0 -4.5c0.5 -1.5 2 -3 4 -3Z"
            >
              <animate fill="freeze" attributeName="stroke-dashoffset" dur="0.6s" values="62;0" />
            </path></svg
        ></span>
        <span class="text">+66 922727906</span>
        <button class="copy" @click="copyText('+66 922727906')">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24">
            <g
              fill="none"
              stroke="currentColor"
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
            >
              <path
                d="M7 9.667A2.667 2.667 0 0 1 9.667 7h8.666A2.667 2.667 0 0 1 21 9.667v8.666A2.667 2.667 0 0 1 18.333 21H9.667A2.667 2.667 0 0 1 7 18.333z"
              />
              <path d="M4.012 16.737A2 2 0 0 1 3 15V5c0-1.1.9-2 2-2h10c.75 0 1.158.385 1.5 1" />
            </g>
          </svg>
        </button>
      </div>

      <!-- Social -->
      <p class="social-text">You may also find me on these platforms!</p>

      <div class="socials">
        <!-- GitHub -->
        <a href="https://github.com/jchukkarin" target="_blank" class="social-btn">
          <img
            src="https://img.icons8.com/?size=100&id=62856&format=png&color=000000"
            alt="GitHub"
            class="icon-img"
          />
        </a>

        <!-- Facebook -->
        <a href="https://www.facebook.com/chukkarin.junchang/" target="_blank" class="social-btn">
          <img
            src="https://img.icons8.com/?size=100&id=uLWV5A9vXIPu&format=png&color=000000"
            alt="Facebook"
            class="icon-img"
          />
        </a>

        <!-- Instagram -->
        <a href="https://www.instagram.com/chukkarin_junchang/" target="_blank" class="social-btn">
          <img
            src="https://img.icons8.com/?size=100&id=Xy10Jcu1L2Su&format=png&color=000000"
            alt="Instargram"
            class="icon-img"
          />
        </a>
      </div>
    </div>
  </section>
</template>
<style scoped>
.contact {
  background: var(--bg);
  padding: 100px 20px;
  display: flex;
  justify-content: center;
  text-align: center;
}

.container {
  max-width: 700px;
}

.tagline {
  background: var(--card);
  padding: 6px 12px;
  border-radius: 20px;
  font-size: 14px;
  font-weight: 600;
}

.desc {
  margin-top: 20px;
  font-size: 18px;
  color: var(--subtext);
  line-height: 1.8;
  max-width: 600px;
}

/* contact item */
.contact-item {
  margin-top: 25px;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  font-size: 22px;
  font-weight: bold;
}

.icon {
  width: 24px;
  height: 24px;
  color: var(--text); /* เปลี่ยนสีได้ */
}

.icon-img {
  width: 24px;
  height: 24px;
  object-fit: contain;
}

.text {
  color: var(--text);
}

/* copy button */
.copy {
  background: none;
  border: none;
  cursor: pointer;
  font-size: 18px;
}

/* social */
.social-text {
  margin-top: 30px;
  font-size: 18px;
  color: var(--subtext);
  line-height: 1.8;
}

.socials {
  margin-top: 15px;
  display: flex;
  justify-content: center;
  gap: 20px;
  font-size: 20px;
}
.social-btn {
  width: 45px;
  height: 45px;
  border-radius: 50%;
  background: var(--card);
  display: flex;
  align-items: center;
  justify-content: center;
  transition: 0.3s;
}
/* hover effect */
.social-btn:hover {
  transform: translateY(-3px);
}

.social-btn:hover .icon {
  color: #fff;
}
</style>
