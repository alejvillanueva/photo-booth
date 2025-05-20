# Photo Booth
Technical assessment for Gramercy Tech. 

## To Run: 
1. Download ZIP or clone repo onto your device. 
2. In root repo, run the following commands: 
   - `npm i`
   - `npm run build`
   - `npm run preview`
3. Then go to http://localhost:4173/


## Stretch Goals / Additional Features
  ### Features
  1. Photo Gallery
    - I would want to use a state to manage all previous submissions. Most likely using Pinia. 
  2. Create a button to flip image / camera.
  3. Add different backgrounds and filters.
  4. Generate a link to share the image or a way to text it to yourself. 

  ### Code
  1. Use a CSS Framework (Tailwind)
  2. Make sure that code is as DRY as possible.
  
## Thoughts and Process
1. My first approach/initial thought to having a photo booth with those four screens was to have a router but quickly realized that wouldn't be necessary. I could use conditional rendering. This would be better for a single page app that didn't require too much complex logic or data management. 
2. I first created the four main components that would be the different screens (Home, Webcam, Review, Thank You) - adding the main text, divs, and buttons that were in each one roughly where I imagined them needing to be.
2. I continued by making sure that the core functionality was there. I tested that each button switched to the correct screen, that variables were reset, and a name was required to start the experience. 
3. I created some reusable components and focused on styling and making sure the layout was intuitive and flowed. I didn't want the change between screens to be too jarring or unpredictable.
4. I went through each file to make sure my code was clean, understandable, and followed some eslint rules. 

## Limitations and Overall Thoughts
As I've mostly worked in React, my biggest limitation I would say was my knowledge in Vue3. At the beginning, I spent time going through the docs and understanding syntax and terminology that I wasn't familiar with. Honestly, Vue ended up being easy to understand and I found myself quickly knowing what to use for this assessment. It's definitely a powerful framework that I would love to continue to explore and keep learning the in and outs to for efficieny, best practices, and being able to continue to create innovative projects. 

Thank you!

