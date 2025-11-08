---
name: Custom template
about: Describe this issue template's purpose here.
title: ''
labels: ''
assignees: ''

---

<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE html>
<html b:version='2' xmlns='http://www.w3.org/1999/xhtml' xmlns:b='http://www.google.com/2005/gml/b' xmlns:data='http://www.google.com/2005/gml/data' xmlns:expr='http://www.google.com/2005/gml/expr'>
<head>
  <meta charset="UTF-8"/>
  <meta content='width=device-width, initial-scale=1' name='viewport'/>
  <title>Online Upload Hub</title>
  <link href='https://fonts.googleapis.com/css2?family=Roboto:wght@400;500;700&display=swap' rel='stylesheet'>

  <!-- STM-Like CSS -->
  <style>
    *{margin:0;padding:0;box-sizing:border-box;}
    body{font-family:'Roboto', Arial, sans-serif;background:#f9f9f9;color:#333;}
    a{text-decoration:none;color:inherit;}

    /* Header */
    header{background:#1e90ff;color:#fff;padding:15px 20px;display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;box-shadow:0 3px 6px rgba(0,0,0,0.1);}
    header h1{font-size:28px;font-weight:700;}
    nav ul{display:flex;list-style:none;flex-wrap:wrap;}
    nav ul li{margin-left:20px;}
    nav ul li a{color:#fff;font-weight:500;transition:.3s;}
    nav ul li a:hover{color:#ffeb3b;}
    .search-bar{margin-left:20px;}
    .search-bar input[type="text"]{padding:6px;border-radius:3px;border:none;}
    .search-bar input[type="submit"]{padding:6px 12px;background:#ffeb3b;color:#1e90ff;border:none;border-radius:3px;font-weight:bold;cursor:pointer;transition:.3s;}
    .search-bar input[type="submit"]:hover{background:#ffd700;}

    /* Hero */
    .hero{background:#f0f8ff;padding:80px 20px;text-align:center;position:relative;overflow:hidden;}
    .hero h2{font-size:36px;color:#1e90ff;margin-bottom:15px;transition:.3s;}
    .hero h2:hover{color:#104e8b;}
    .hero p{font-size:18px;margin-bottom:25px;}
    .btn{background:#1e90ff;color:#fff;padding:14px 30px;border-radius:6px;font-weight:bold;display:inline-block;transition:.3s;}
    .btn:hover{background:#104e8b;transform:translateY(-3px);}

    /* Container */
    .container{display:flex;flex-wrap:wrap;justify-content:space-between;padding:20px;}
    .main-content{flex:0 0 70%;max-width:70%;}
    .sidebar{flex:0 0 28%;max-width:28%;background:#fff;padding:20px;border-radius:8px;margin-bottom:20px;box-shadow:0 3px 6px rgba(0,0,0,0.05);}

    /* Posts */
    .post{background:#fff;padding:20px;margin-bottom:20px;border-radius:8px;transition:.3s;}
    .post h3{color:#1e90ff;margin-bottom:10px;}
    .post p{font-size:15px;line-height:1.6;}
    .post:hover{box-shadow:0 6px 15px rgba(0,0,0,0.15);transform:translateY(-3px);}

    /* Featured Slider */
    #featured-slider{position:relative;overflow:hidden;border-radius:8px;margin-bottom:30px;}
    .slide-item{min-width:100%;padding:20px;background:#e6f2ff;color:#104e8b;text-align:center;font-weight:bold;font-size:18px;display:none;}

    /* Upload Section */
    .upload-section{background:#fff;padding:20px;border-radius:8px;margin-bottom:30px;box-shadow:0 3px 10px rgba(0,0,0,0.1);}
    .upload-section h3{color:#1e90ff;margin-bottom:15px;}
    .upload-section iframe{width:100%;height:400px;border:none;border-radius:5px;}

    /* Sidebar */
    .sidebar h3{color:#1e90ff;margin-bottom:15px;}
    .sidebar ul{list-style:none;}
    .sidebar ul li{margin-bottom:10px;}
    .sidebar ul li a{color:#333;transition:.3s;}
    .sidebar ul li a:hover{color:#1e90ff;}

    /* Footer */
    footer{background:#1e90ff;color:#fff;text-align:center;padding:25px 0;margin-top:20px;font-size:14px;box-shadow:0 -3px 6px rgba(0,0,0,0.1);}

    @media(max-width:900px){.main-content,.sidebar{flex:0 0 100%;max-width:100%;} nav ul{flex-direction:column;margin-top:10px;} nav ul li{margin-left:0;margin-bottom:10px;} .search-bar{margin-left:0;margin-top:10px;}}
  </style>
</head>

<body>
  <!-- Header -->
  <header>
    <h1>Online Upload Hub</h1>
    <nav>
      <ul>
        <li><a expr:href='data:blog.homepageUrl'>Home</a></li>
        <li><a href='#'>Upload</a></li>
        <li><a href='#'>About</a></li>
        <li><a href='#'>Contact</a></li>
      </ul>
    </nav>
    <div class="search-bar">
      <form expr:action='data:blog.homepageUrl' method='get'>
        <input type="text" name="q" placeholder="Search..."/>
        <input type="submit" value="Go"/>
      </form>
    </div>
  </header>

  <!-- Hero Section -->
  <section class="hero">
    <h2>Upload and Share Your Files Easily</h2>
    <p>Fast, secure, and free file uploads.</p>
    <a href='#' class="btn">Upload Now</a>
  </section>

  <!-- Main Content -->
  <div class="container">
    <div class="main-content">
      <!-- Dynamic Featured Slider -->
      <div id="featured-slider">
        <b:loop values='data:posts' var='post'>
          <div class="slide-item">
            <a expr:href='data:post.url'><data:post.title/></a>
          </div>
        </b:loop>
      </div>

      <script>
        let slides=document.querySelectorAll("#featured-slider .slide-item");
        let index=0;
        function showSlide(){
          slides.forEach((s)=>s.style.display="none");
          if(slides.length>0){slides[index].style.display="block";index=(index+1)%slides.length;}
        }
        showSlide();
        setInterval(showSlide,3000);
      </script>

      <!-- Google Drive Upload Section -->
      <div class="upload-section">
        <h3>Upload Your File</h3>
        <iframe src="https://docs.google.com/forms/d/e/YOUR_FORM_ID/viewform?embedded=true"></iframe>
      </div>

      <!-- Blog Posts -->
      <b:section id='main' class='main' maxwidgets='1' showaddelement='yes'>
        <b:widget id='Blog1' type='Blog' title='Recent Posts' />
      </b:section>
    </div>

    <!-- Sidebar -->
    <div class="sidebar">
      <b:section id='sidebar' class='sidebar' maxwidgets='5' showaddelement='yes'>
        <b:widget id='Label1' type='Label' title='Categories' />
        <b:widget id='Archive1' type='BlogArchive' title='Archives' />
        <b:widget id='Text1' type='Text' title='About' content='Welcome to Online Upload Hub. Upload and share files easily!' />
        <b:widget id='PopularPosts1' type='PopularPosts' title='Popular Posts' />
      </b:section>
    </div>
  </div>

  <!-- Footer -->
  <footer>
    <p>&copy; 2025 Online Upload Hub. All Rights Reserved.</p>
  </footer>
</body>
</html>
