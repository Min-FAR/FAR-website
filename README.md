from zipfile import ZipFile
import os

# Create the HTML content
html_content = """<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>FAR - First Aid Rider</title>
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', sans-serif;
      background-color: #fefefe;
      color: #222;
    }
    header {
      background-color: #c62828;
      color: white;
      padding: 2rem;
      text-align: center;
    }
    .section {
      padding: 2rem;
      max-width: 800px;
      margin: auto;
    }
    .hero {
      background: #fff3f3;
      padding: 2rem;
      border-radius: 1rem;
      box-shadow: 0 2px 6px rgba(0,0,0,0.1);
      margin: 2rem auto;
      text-align: center;
    }
    .hero h2 {
      color: #b71c1c;
    }
    footer {
      background-color: #c62828;
      color: white;
      text-align: center;
      padding: 1rem;
    }
  </style>
</head>
<body>
  <header>
    <h1>FAR – First Aid Rider</h1>
    <p>Ride with Purpose. Respond with Heart.</p>
  </header>

  <section class="section hero">
    <h2>What is FAR?</h2>
    <p><strong>FAR (First Aid Rider)</strong> is a group of volunteer motorcyclists trained in basic first aid.</p>
    <p>We carry medical kits on our bikes and respond to accidents on the road.</p>
    <p>We are <em>not doctors</em>, but we’re often the first ones there when someone needs help.</p>
    <br />
    <h3>Our Mission:</h3>
    <ul style="list-style: none; padding: 0;">
      <li>🛵 Be the first to help at accident scenes</li>
      <li>🩹 Give basic medical aid until ambulance arrives</li>
      <li>🤝 Support riders and the public during emergencies</li>
    </ul>
  </section>

  <footer>
    <p>&copy; 2025 FAR - First Aid Rider. All rights reserved.</p>
  </footer>
</body>
</html>
"""

# Create a README with simple instructions
readme_content = """HOW TO OPEN YOUR FAR WEBSITE

1. Copy this folder to your computer.
2. Double-click the 'index.html' file.
3. Your website will open in the browser!

TO UPLOAD ONLINE (Netlify):
- Visit https://netlify.com
- Login with Google
- Click 'Add new site' > 'Deploy manually'
- Drag and drop this index.html file
- Done! Your site is live.
"""

# Save both files to a directory
folder_path = "/mnt/data/far_website"
os.makedirs(folder_path, exist_ok=True)

with open(os.path.join(folder_path, "index.html"), "w", encoding="utf-8") as f:
    f.write(html_content)

with open(os.path.join(folder_path, "README.txt"), "w", encoding="utf-8") as f:
    f.write(readme_content)

# Create a zip file
zip_path = "/mnt/data/FAR_FirstAidRider_Site.zip"
with ZipFile(zip_path, 'w') as zipf:
    zipf.write(os.path.join(folder_path, "index.html"), arcname="index.html")
    zipf.write(os.path.join(folder_path, "README.txt"), arcname="README.txt")

zip_path
