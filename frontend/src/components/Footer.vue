<template>
  <footer>
    <div class="container-fluid">
      <div class="row">
        <!-- left footer section: quick link -->
        <div class="col-lg-4 col-md-4">
          <h3>Quick Links</h3>
          <ul class="list-unstyled">
            <li>
              <a href="/" style="color: #fff;">Home Page</a>
            </li>
            <li>
              <a href="/search" style="color: #fff;">Search House</a>
            </li>
            <li>
              <a href="#" style="color: #fff;">Back to top</a>
            </li>
          </ul>
        </div>
        <!-- middle footer section: thanks to -->
        <div class="col-lg-4 col-md-4">
          <h3>Thanks to</h3>
          <ul class="list-unstyled">
            <li>
              <a href="https://google.com" style="color: #fff;">Google</a>
            </li>
            <li>
              <a href="https://getbootstrap.com/" style="color: #fff;">Bootstrap</a>
            </li>
            <li>
              <a href="https://udemy.com" style="color: #fff;">Udemy</a>
            </li>
          </ul>
        </div>
        <!-- right footer section: contact us -->
        <div class="col-lg-4 col-md-4">
          <h3>Contact us</h3>
          <ul class="list-unstyled">
            <li>TEL: +61 123456</li>
            <li>Email: unsw@mail.com</li>
            <li>Address: UNSW, Kensington</li>
          </ul>
        </div>
      </div>
      <!-- social media icons -->
      <a href="https://facebook.com" style="color: #fff;"><i class="social-icon fab fa-facebook-f"></i></a>
      <a href="https://twitter.com" style="color: #fff;"><i class="social-icon fab fa-twitter"></i></a>
      <a href="https://instagram.com" style="color: #fff;"><i class="social-icon fab fa-instagram"></i></a>
      <a href="https://www.unsw.edu.au/" style="color: #fff;"><i class="social-icon fas fa-envelope"></i></a>
      
      <p>© All right Reversed. Bomb Shrimper.</p>
    </div>
  </footer>
</template>

<script>
export default {
  name: "Footer"
};
</script>

<style scoped>
footer {
  padding-top: 3rem;
  padding-bottom: 3rem;
  background-color: #3c9d9b;
  color: white;
}
.social-icon {
  margin: 30px 20px;
}
</style> 