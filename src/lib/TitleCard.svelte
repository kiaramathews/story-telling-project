<script>
   let { title, subtitle } = $props();
</script>


<div class="title-card">
   <div class="content">
       <h1>{title}</h1>
       <p>{subtitle}</p>
   </div>
</div>


<style>
   .title-card { 
     background-image: url('https://i.postimg.cc/BbZcjpjB/Untitled-design-7.png');
    background-size: cover;
    background-position: center;
       height: 100vh;
       display: flex;
       justify-content: center;
       align-items: center;
       text-align: center;
       padding: 2rem;
       box-sizing: border-box;
       font-family: 'Playfair Display', serif;
   }


   .content {
       max-width: 700px;
       background-color: #413d3d;
       padding: 2rem;
       border: 10px solid #9d0e0e;
       border-radius: 2rem;
       box-shadow: 16px 16px #67070a;
   }


   h1 {
       font-size: 3rem;
       margin: 0;
       color: #070202;
       text-shadow: 1px 1px 0 #820d0f;
   }


   p {
       font-size: 1.3rem;
       color: #f7f5eb;
       margin-top: 1rem;
   }


   @media (max-width: 600px) {
       h1 {
           font-size: 2.2rem;
       }


       p {
           font-size: 1.1rem;
       }
   }
</style>
