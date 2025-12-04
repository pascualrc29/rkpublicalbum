Rodger & Katherine - Digital Wedding Guestbook

A real-time, responsive digital guestbook web application that allows wedding guests to capture, upload, and view photos instantly. It includes a separate Admin Dashboard for the couple to manage memories.

🌟 Features

📸 Guestbook (index.html)

Instant Uploads: Guests can take photos directly or upload from their gallery.

Client-Side Compression: Photos are automatically compressed before uploading to save data and storage.

Live Gallery: Real-time updates as new photos are added.

Interactive UI: Swipeable lightbox gallery with thumbnail navigation.

Mobile-First Design: Optimized for all devices with a native app-like feel.

Anonymous Auth: No login required for guests (uses Firebase Anonymous Auth).

🛡️ Admin Dashboard (admin.html)

Secure Access: Protected by Google Sign-In.

Content Moderation:

Hide/Unhide: Toggle visibility of photos without deleting them. Hidden photos instantly disappear from the public guestbook.

Delete: Permanently remove unwanted photos.

Storage Monitor: Visual indicator of database usage with a toggle for Spark (Free) vs. Blaze plan limits.

Status Indicators: Quickly see which photos are hidden.

🚀 Setup & Configuration

1. Firebase Setup

This project requires a Firebase project.

Go to the Firebase Console.

Create a new project.

Authentication:

Enable Anonymous (for guests).

Enable Google (for admin access).

Firestore Database:

Create a database in Test Mode (or configure rules to allow public read/write).

Important: Ensure your rules allow guests to write but not update/delete others' data.

2. Google Sign-In Configuration (For Admin)

In Firebase Console -> Authentication -> Settings -> Authorized domains.

Add your hosting domain (e.g., your-site.netlify.app or your-username.github.io).

Note: Without this step, Admin login will fail.

3. Deploying the Code

This is a static web application. You can host it on Netlify, GitHub Pages, or Vercel.

Edit Configuration:

Open index.html and admin.html.

Replace the firebaseConfig object with your own credentials from Project Settings.

const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_PROJECT_ID.firebasestorage.app",
  messagingSenderId: "YOUR_SENDER_ID",
  appId: "YOUR_APP_ID"
};


Upload: Upload both index.html and admin.html to your hosting provider.

📂 Project Structure

index.html: The public-facing site. Contains the landing page, camera/upload logic, and the photo gallery. It filters out any photo where isHidden == true.

admin.html: The private dashboard. Contains login logic and management tools. It sees all photos.

🛠️ Tech Stack

Frontend: HTML5, React (via CDN), Tailwind CSS (via CDN).

Backend: Firebase Authentication, Cloud Firestore.

Icons: Lucide React / Inline SVGs.

⚠️ Admin Access Note

The Admin Dashboard uses Google Sign-In. Ensure the Google account you intend to use is added as a user in your Firebase Authentication tab, or simply sign in once to create the user record. To restrict access strictly to specific emails, you would need to implement Firestore Security Rules based on request.auth.token.email.
