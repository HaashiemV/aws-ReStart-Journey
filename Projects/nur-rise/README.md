Nur-Rise | Islamic Prayer & Thikr Tracker

A personal web application designed to encourage consistency in daily worship through prayer tracking, thikr counting and personal reflection.

Live application: https://d1m8pbscr3biya.cloudfront.net/#home

Project Overview

Nur-Rise was created as a personal project to make daily Islamic worship tracking simple and accessible across desktop and mobile devices.

The application focuses on creating a simple, welcoming experience that encourages consistent daily habits.

Features

- Five daily prayer tracking.
- Four thikr counters.
- Personal reflection journal.
- Dark mode.
- Daily reminder section.
- Progress cards.
- Responsive mobile and desktop layout.
- Browser-based progress persistence using Local Storage.

Technologies Used

Technology| Purpose
HTML| Application structure
CSS| Styling and responsive layout
JavaScript| Application functionality
Amazon S3| Static website hosting
Amazon CloudFront| Content delivery
Browser Local Storage| Saving user progress locally

AWS Architecture

The application follows a simple static website hosting architecture:

1. User
↓
2. Amazon CloudFront – Delivers website content.
↓
3. Amazon S3 – Stores the static website files.
↓
4. HTML, CSS and JavaScript – Builds the application.
↓
5. Browser Local Storage – Saves the user's progress locally.

CloudFront delivers the website content, while Amazon S3 stores the static website files.

User progress is saved locally in the browser using Local Storage.

Important Implementation Details

- No user account or authentication system is currently implemented.
- Progress is stored locally in the browser.
- Data does not automatically synchronise between devices or browsers.
- No shared backend database is currently implemented.

Skills Demonstrated

- Static website development.
- AWS S3 website hosting.
- CloudFront content delivery.
- Front-end development.
- Browser Local Storage.
- Responsive user interface design.
- Project planning and implementation.

Potential Future Improvements

- User authentication.
- Cloud-based progress synchronisation.
- Database integration.
- Improved reminders and notifications.
- Additional Islamic learning resources.

Project Status

Deployed – Static website MVP

This project demonstrates practical application development and AWS hosting using managed cloud services.

---

Built as a personal project combining technology, learning and Islamic daily habits.
