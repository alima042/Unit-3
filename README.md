# Lab 6: Instaparse (Parts 1 & 2)

**Student Name:** Alfredo Lima
**Panther ID:** 5867669
**Section:** COP4655
**Semester:** Spring
**Email:** alfredn.lima210@gmail.com

---

## Overview

This repository contains the complete, working code for **Lab 6 - Instaparse**, satisfying all the requirements for both Part 1 and Part 2. The project is an Instagram-like social media clone built natively for iOS using **Swift** and **UIKit**. 

It integrates the **Parse Swift SDK** to communicate with a remote Back4App Parse Server, allowing users to securely sign up, log in, create posts (with images and captions), and view a chronological feed of posts from all users.

## Features Implemented

* **User Authentication:** 
  * Full user registration and secure login via `ParseUser`.
  * Persistent session checks on app launch using `SceneDelegate`.
  * Proper session termination on Log Out.
* **Feed & Data Querying:** 
  * Fetches the latest posts dynamically from the Parse Server using `Post.query()`.
  * Part 2 Constraint: The feed leverages `createdAt` comparisons to **only show posts created within the last 24 hours**, limited to a maximum of 10 posts.
  * Pull-to-refresh functionality seamlessly updates the data source.
* **Hardware & Media Flow:**
  * Uses `PHPickerViewController` for seamless photo library access.
  * Checks device capabilities and uses `UIImagePickerController` to handle live camera capture for new posts.
* **BeReal-style Blur Effect (Part 2):**
  * The custom `PostCell` implements conditional UI logic (`blurView`).
  * If the currently logged-in user has *not* posted anything within the last 24 hours, the `blurView` obscures the images of posts on their feed. Once they create a post, their `lastPostedDate` object updates in the Parse DB, instantly revealing the feed images.

## Setup & Running Instructions

The project has been prepared meticulously so that **no additional changes or file additions** are required by the cloning user to compile it successfully.

1. **Clone the Repository:**
   Clone this repository to your local macOS machine running a recent version of Xcode.
2. **Open the Project:**
   Navigate into the directory and open `lab-insta-parse.xcodeproj`.
3. **Wait for Package Resolution:**
   Since the project relies on **Swift Package Manager (SPM)**, give Xcode a few moments to automatically resolve and fetch the required dependencies:
   * `Parse-Swift`
   * `Alamofire`
   * `AlamofireImage`
4. **Build and Run:**
   * Select a target simulator (e.g., iPhone 14 Pro).
   * Press `Cmd + R` or click the Play button.
   * *Note: If testing the camera functionality, it is recommended to run the app on a physical iOS device, as Basic Simulators typically do not have live camera feeds enabled.*

## Architecture Notes
* **Data Models:** `User.swift` and `Post.swift` natively conform to `ParseUser` and `ParseObject` respectively, storing strings, dates, and `ParseFile` image references.
* **API Keys:** The `AppDelegate` securely initializes using the remote App ID and Client Key from the Back4App instance provisioned during Unit 2.
* **Code Authorship:** All custom logic requested in the `TODO: Pt 1` and `TODO: Pt 2` segments was injected delicately without altering or destructing the original skeleton constraints and outlets provided in the Lab structure.

## License

    Copyright 2023 Alfredo Lima

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
---
*Created for COP4655 - Advanced iOS Programming.*
