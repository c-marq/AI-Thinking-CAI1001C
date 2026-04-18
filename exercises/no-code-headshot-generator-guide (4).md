# Step-by-Step Guide: Build a No-Code Professional Headshot Generator

**Transform casual photos into professional headshots using Google AI Studio's Build Mode and Nano Banana**

---

## What You'll Build

A live web application that transforms casual selfies into professional corporate headshots using AI, deployed and accessible to anyone via a URL. Built entirely through "vibe coding" by describing what you want in plain English.

**Time Required:** 20 to 30 minutes
**Cost:** Free for building and testing (Nano Banana includes a free tier of ~500 image generations per day through AI Studio, no credit card required). Cloud Run deployment requires a Google Cloud project with billing enabled, but includes 2 million free requests per month.
**Coding Required:** None (the Antigravity coding agent generates all code for you)
**Tools Needed:** Google account, web browser, 3 to 5 test photos

---

## Prerequisites

- A Google account (regular Gmail works fine)
- 3 to 5 portrait photos for testing (selfies, casual photos)
- Web browser (Chrome, Firefox, Safari, or Edge)
- Basic understanding of what makes a professional headshot
- A Google Cloud project with billing enabled (only required for the deployment step, not for building or testing)

---

## Step 1: Access Google AI Studio and Open Build Mode

**Actions:**

1. Open your web browser
2. Navigate to: https://aistudio.google.com
3. Click "Sign in" in the top right and use your Google account
4. On the left sidebar you'll see five sections: Home, Playground, Build, Dashboard, Documentation
5. Click **Build**
6. You'll land on the Build mode interface, which shows the App Gallery, an "I'm Feeling Lucky" button, and a large prompt input area

**Why This Matters:**

Build mode is Google's "vibe coding" environment, now powered by the Antigravity coding agent. You describe an app in plain English and the agent generates a complete React application with frontend, server-side Node.js runtime, secrets management, and Gemini API integration. Playground is for testing prompts. Build is for creating real, deployable applications.

**Common Mistake:**

Don't click Playground or Home looking for a "build app" button. Build mode lives in its own dedicated section in the left sidebar.

---

## Step 2: Start a New Project and Add Image Generation Capability

**Actions:**

1. In the Build mode prompt area, look for the **AI Chips** options near the input box
2. Click the **Image Generation** chip to tell the agent your app will use Nano Banana image generation
3. This adds the image generation capability to your project automatically
4. Your cursor is now in the prompt input box, ready for your description

**Why This Matters:**

AI Chips pre-configure capabilities in your project. By selecting Image Generation, you're telling the Antigravity agent to scaffold your app with Nano Banana already wired up. This removes the guesswork of manually specifying model strings or API integration details.

**Common Mistake:**

If you skip the Image Generation chip and only describe what you want, the agent will usually figure it out from context. But selecting the chip first gives more reliable results and faster scaffolding.

---

## Step 3: Write Your Complete App Description Prompt

**Actions:**

1. In the prompt input area, paste this description exactly:

```
Build a professional headshot generator web application with the following features:

1. IMAGE UPLOAD: Clean, drag-and-drop interface for uploading photos (JPG, PNG). Display uploaded image preview on the page.

2. AI TRANSFORMATION: Use Nano Banana (Gemini 2.5 Flash Image, model: gemini-2.5-flash-image) to transform the uploaded casual photo into a professional corporate headshot. Send the uploaded image as a reference and use this transformation prompt:

"Create a photorealistic, high-resolution corporate headshot of the individual from the provided reference image, framed from the chest up. Render the subject with a confident yet approachable expression, featuring a subtle and genuine smile. Ensure their posture is upright and relaxed, with shoulders slightly angled towards the camera.

Dress the subject in sharp, contemporary business attire: a well-tailored dark suit jacket in navy blue or charcoal gray, worn over a crisp white or light-blue collared shirt. The clothing should appear high quality, well fitted, and free of wrinkles.

Use a classic studio lighting scheme with soft loop key light, subtle fill light, and a gentle rim light from behind for separation. Distinct catchlights should be visible in the eyes.

Place the subject against a seamless neutral-gray studio background with a subtle gradient that is darker at the bottom and lighter towards the top.

Emulate the quality of a professional DSLR with an 85mm prime portrait lens at f/2.8, producing tack-sharp focus on the subject and softly blurred background bokeh. The output should be high resolution, sharp, and free of digital artifacts. Preserve the subject's facial identity from the reference image."

3. USER INTERFACE:
   - Professional, clean design with navy, gray, and white color scheme
   - Clear "Transform to Professional Headshot" button
   - Loading indicator during AI processing showing "Generating your headshot..."
   - Side-by-side comparison of original and transformed images
   - Download button for the generated headshot
   - Mobile responsive layout

4. USER EXPERIENCE:
   - Helpful instructions: "Upload a clear, well-lit photo with your face visible for best results"
   - Show processing status with estimated time (10 to 20 seconds)
   - Display a friendly success message when complete
   - Allow users to upload another photo without refreshing the page
   - Show a clear error message if the API call fails

Generate the complete working application with the Nano Banana integration handled in geminiService.ts.
```

2. Review for typos
3. Click the **Build** button below the prompt area

**Why This Matters:**

The prompt explicitly references **Nano Banana** and the model string **gemini-2.5-flash-image**. This is the original Nano Banana model, which has a genuine free tier (approximately 500 image generations per day through AI Studio) with no credit card required. Newer models like Nano Banana 2 and Nano Banana Pro offer higher resolution and faster speeds, but their API access requires paid billing. For a tutorial where you need to build and test without spending money, the original Nano Banana is the right choice.

**Common Mistake:**

Don't write a vague description like "make a photo editor app." The Antigravity agent works best when you give it specific UI requirements, the exact model to use, and the transformation prompt as a quoted block. A detailed first prompt produces a working app on the first try and saves you iteration time.

---

## Step 4: Watch the Antigravity Agent Build Your Application

**Actions:**

1. After clicking Build, the agent begins working (typically 30 to 90 seconds)
2. The right-hand panel shows two tabs: **Preview** and **Code**
3. Watch the Code tab populate with files including:
   - `geminiService.ts` (contains your Nano Banana integration logic)
   - React component files for the UI
   - Styling files
   - Configuration files
4. When generation completes, the Preview tab shows your live app running

**What the agent is doing:**

- Scaffolding a React frontend (the default; Angular is also available in Settings)
- Writing the Gemini API integration in `geminiService.ts` using the GenAI TS SDK
- Building drag-and-drop upload, loading states, and download functionality
- Wiring everything together with the transformation prompt embedded

**Why This Matters:**

The Antigravity agent maintains context across your entire project. Unlike older code generation tools that produced isolated snippets, it understands how all your files connect. This means later iterations won't break existing functionality, which is critical for non-coders who can't manually fix broken integrations.

**Common Mistake:**

Don't refresh the browser or navigate away while generation is running. If you see warnings or partial errors during generation, wait for the agent to finish. It usually self-corrects.

---

## Step 5: Test Your Application in the Preview Panel

**Actions:**

1. Click the **Preview** tab in the right panel
2. You should see your full application running live
3. Test the upload functionality:
   - Drag a test photo into the upload area, or click to browse
   - Verify the photo preview displays
4. Click "Transform to Professional Headshot"
5. Watch the loading indicator (Nano Banana typically completes in 10 to 20 seconds)
6. View the generated headshot
7. Test the download button

**Checkpoint:** At this point, you should see:
- Your original photo on the left
- A professionally transformed headshot on the right
- A working download button beneath the result

If the transformation fails, check the Code tab for error messages. The most common cause is the model name not being recognized. Make sure the code references `gemini-2.5-flash-image` exactly.

**What to examine in the results:**

- Does the interface look clean and professional?
- Does the upload work smoothly (drag and drop, click to browse)?
- Does the transformed photo preserve the subject's identity?
- Are the lighting and background as described in the prompt?
- Does the download produce a usable image file?

**Why This Matters:**

The Preview panel runs the same code that will deploy to Cloud Run. Testing here is free (it uses your AI Studio free tier allocation). Catching issues now saves redeployment cycles later.

**Common Mistake:**

Don't test with only one perfect photo. Try edge cases: a blurry photo, a photo taken in low light, a side profile, a group photo. This shows you how the app behaves with real-world input quality and helps you decide whether to add validation messages.

---

## Step 6: Refine Your Application Using the Chat Panel or Annotation Mode

**Actions:**

**To refine using the chat panel:**

1. Find the chat input at the bottom of the Build mode interface
2. Type plain-English change requests like:
   - "Make the upload area larger and add a dashed border"
   - "Change the loading message to say 'Polishing your professional look...'"
   - "Add a dropdown to select background color: gray, white, or light blue"
3. The agent updates the relevant files and the Preview refreshes

**To refine using Annotation Mode:**

1. In the Preview panel, look for the **Annotation** toggle (pencil or highlight icon)
2. Click the UI element you want to change directly in the live preview
3. Type your change request in the popup
4. Click **Add to chat**, which sends a screenshot of the annotated element along with your request
5. The agent makes the targeted change

**Why This Matters:**

Annotation Mode is the fastest way to make visual changes because the agent receives both your description and a screenshot showing exactly what you're pointing at. This eliminates the "which button did you mean?" problem that plain text prompts sometimes produce.

**Common Mistake:**

Don't bundle five changes into one request. Make one change, verify it works in Preview, then make the next. If something breaks, you'll know exactly which request caused it and can ask the agent to revert that specific change.

---

## Step 7: Set Up Your Google Cloud Project for Publishing

**Actions:**

If this is your first time publishing from Build mode, do this once:

1. Open a new tab and go to https://console.cloud.google.com
2. Create a new project or select an existing one
3. Enable billing on the project (required for Cloud Run; if this is your first Google Cloud account, you get $300 in free trial credits)
4. Return to AI Studio Build mode

If you've published before:

1. Skip directly to Step 8

**Why This Matters:**

Cloud Run requires a Google Cloud project with billing enabled, but the free tier includes 2 million requests per month. Combined with the $300 new-customer credit, students can deploy and run small apps for months without paying anything.

**Common Mistake:**

Don't skip enabling billing. Cloud Run won't deploy without it, even on the free tier. The billing setup is a requirement, not a charge. Your first 2 million requests each month are free regardless.

---

## Step 8: Publish Your Application to Cloud Run

**Actions:**

1. In Build mode, look for the **Publish** button in the top right area of the screen
2. Click **Publish**
3. A publish dialog opens with several options:
   - **Cloud Run:** Deploy as a live web app with a public URL (this is what we want)
   - **GitHub:** Export to a GitHub repository
   - **Download:** Save the project as a ZIP file
4. Select **Cloud Run** and configure these settings:
   - **Google Cloud Project:** Select the project from Step 7 (if this is your first publish, click "Import project" to find it)
   - **Service name:** Use lowercase with hyphens, e.g., `pro-headshot-gen`
   - **Region:** Choose one close to your users (e.g., `us-central1`)
   - **Authentication:** Select "Allow unauthenticated invocations" so anyone can use your app
5. Click **Publish** (or **Deploy app** in the dialog)
6. Wait 2 to 4 minutes while Google packages the code, builds the container, and deploys
7. When complete, you'll see your live URL, formatted like `https://pro-headshot-gen-xxxxx.run.app`
8. Click the URL to open your live app

**What happens behind the scenes:**

- Google AI Studio packages your full-stack app
- Your Gemini API key is securely transferred to Cloud Run as a server-side environment variable (it never appears in client code)
- Cloud Run builds a container, sets up auto-scaling, and configures HTTPS
- Your app gets a globally accessible URL with SSL encryption

**Why This Matters:**

The API key handling is important. When you deploy from Build mode to Cloud Run, your key is stored server-side, meaning users of your app never see it. This is the same pattern professional developers use, handled automatically for you.

**Common Mistake:**

Don't publish without testing in the Preview panel first. Each republish takes a few minutes, so catching issues early saves significant time. Also, remember that all API calls from your published app use **your** Gemini API key, so your usage will count against your project's quota. See Step 11 for cost monitoring.

---

## Step 9: Test Your Live App

**Actions:**

1. Copy your live URL from the deployment confirmation
2. Open an **incognito or private browsing window**
3. Paste the URL and press Enter
4. Test as a first-time user:
   - Does the page load quickly?
   - Upload a test photo
   - Click transform and wait for the result
   - Download the generated image
5. Test on your phone:
   - Open the URL in your mobile browser
   - Verify the upload works on touch screens
   - Check the layout is responsive
6. Try 3 to 5 different photos to confirm consistency

**Checkpoint:** Your live app should behave identically to the Preview panel version. If transformations work in Preview but fail on the live URL, the most likely cause is an API key or billing issue in your Google Cloud project.

**Why testing in incognito matters:**

Incognito mode shows you exactly what new users see with no cached files or saved sessions. Issues you don't notice while logged into AI Studio become obvious when you test as an anonymous visitor.

**Common Mistake:**

Don't assume "if it works in Preview, it works everywhere." Network latency, browser differences, and mobile touch behavior can all surface issues that didn't appear in the Build mode preview. Always test the live URL.

---

## Step 10: Share Your App and Gather Feedback

**Actions:**

1. Take screenshots showing the upload screen, a before/after comparison, and the download button
2. Share your URL with friends, classmates, or colleagues who need a professional photo
3. Post on LinkedIn with a short description and your URL
4. Ask for specific feedback:
   - "Does the transformation look natural?"
   - "Would you actually use this for your LinkedIn photo?"
   - "What would make this more useful?"

**Why This Matters:**

Building the app is only half the value. Real user feedback reveals issues and feature ideas you can't predict from solo testing. Even 10 users who try your app give you more insight than 100 hours of testing alone.

**Common Mistake:**

Don't deploy and walk away. An app without users is code sitting on a server generating zero value.

---

## Step 11: Monitor Usage and Costs

**Actions:**

1. Go to https://console.cloud.google.com
2. Navigate to **Cloud Run** → your service → **Metrics**
3. Monitor request count, error rate, and response times
4. Navigate to **Billing** → **Reports** to view actual costs
5. Set a budget alert: **Billing** → **Budgets & alerts** → **Create budget**, set it to $5 or $10/month with email notifications

**Understanding the cost model:**

Two cost layers apply to your deployed app:

**Cloud Run hosting:** Free for the first 2 million requests per month. For a small headshot app, this covers more traffic than you'll realistically get.

**Nano Banana API usage:** Each image transformation is an API call. Nano Banana (gemini-2.5-flash-image) costs approximately **$0.039 per image** on the paid tier. However, through AI Studio, the free tier provides roughly 500 image generations per day with no credit card required.

Here's what that looks like in practice:
- Testing in Preview (Build mode): free, uses your AI Studio free tier
- Deployed app with 10 users per day: approximately $0.39/day, or about $12/month
- Deployed app with 100 users per day: approximately $3.90/day, or about $117/month

Set a budget alert before sharing your app publicly so you're not surprised by unexpected usage.

**Why This Matters:**

Honest cost expectations matter more than optimistic ones. For building and testing, you'll spend nothing. For deployment, costs are real but small for low-traffic apps. Budget alerts protect you from surprise bills if your app goes viral.

**Common Mistake:**

Don't ignore cost monitoring. While individual transformations cost pennies, high usage adds up. Set the budget alert before you share the URL widely.

---

## Step 12: Iterate Based on Feedback

**Actions:**

1. Return to Build mode (your project is auto-saved in your Google Drive)
2. Use the chat panel to make changes based on user feedback
3. Test changes in Preview to confirm they work

**Pushing updates to your live app:**

This is where the current Build mode experience gets bumpy. After making edits, you might expect a "Republish" button to appear, but in practice it often doesn't. The Publish button stays the same, and clicking it again may not update your live site. This is a known issue that multiple developers have reported on the Google AI Developers Forum.

**If clicking Publish doesn't update your live site, try these workarounds:**

1. **Publish to the same project again:** Click Publish, select the same Google Cloud project and the same service name. This should overwrite the existing Cloud Run service with your updated code.
2. **Check Cloud Run directly:** Go to https://console.cloud.google.com → Cloud Run → your service. Look at the "Revisions" tab to see if a new revision was created. If the old revision is still serving traffic, click on the new revision and route 100% of traffic to it.
3. **Force a fresh publish:** If nothing else works, try publishing with a slightly different service name (e.g., `pro-headshot-gen-v2`). This creates a new Cloud Run service with a new URL. Not ideal, but it reliably gets your updated code live.

**Why this matters to acknowledge honestly:**

Build mode's publishing workflow is still maturing. The build-and-test experience inside AI Studio is excellent, but the publish-update cycle has rough edges as of April 2026. Being upfront about this saves you from spending an hour troubleshooting what feels like your own mistake when it's actually a platform limitation.

**Common iteration ideas:**

- "Add a slider to compare before and after side by side"
- "Add image compression before sending to the API to reduce file size"
- "Add a message limiting each user to 3 transformations per session"
- "Let users choose between business formal and business casual attire styles"

**Why This Matters:**

Vibe coding is designed for iteration. Your first version doesn't have to be perfect because changes are fast and the agent maintains context across your entire project. The publish-update workflow will likely improve over time. For now, the workarounds above will get your updates live.

---

## Understanding What You Built

**Your deployed app consists of these components, all generated automatically:**

**Frontend (React application):**
- Drag-and-drop file upload with image preview
- Loading state management during AI processing
- Side-by-side comparison display
- Download functionality for transformed images
- Responsive design for desktop and mobile

**Backend (Node.js server-side logic):**
- Secure API calls to Google's Gemini API using the GenAI TS SDK
- Base64 image encoding/decoding for API transmission
- Error handling for failed API requests or timeouts
- API key stored securely in environment variables

**Cloud Infrastructure (Google Cloud Run):**
- Containerized application
- Auto-scaling from zero to thousands of users
- HTTPS encryption
- Pay-per-use pricing with generous free tier

**AI Model Integration:**
- Nano Banana (Gemini 2.5 Flash Image) for photo transformation
- Your custom transformation prompt embedded in API calls
- SynthID watermarking on all AI-generated images (Google's transparency standard)

---

## Troubleshooting Common Issues

### Issue: "Published app doesn't reflect my latest changes"

**Cause:** The publish-update workflow in Build mode is unreliable as of April 2026. Changes visible in Preview may not propagate to the live Cloud Run site when you click Publish again.
**Solution:** Try publishing to the same project and service name again. If that doesn't work, go to Google Cloud Console → Cloud Run → your service → Revisions tab, and check whether a new revision was created. Route traffic to the new revision manually. As a last resort, publish with a new service name to get a fresh URL with your updated code.

---

### Issue: "Transformations fail with an API error"

**Cause:** API key issue, billing not enabled, or quota exceeded
**Solution:** Verify your Google Cloud project has the Gemini API enabled. Check that billing is active. Confirm you haven't exceeded your daily free tier quota in the AI Studio Dashboard.

---

### Issue: "Generated image doesn't look like the original person"

**Cause:** The transformation prompt may need stronger identity preservation language
**Solution:** Tell the agent: "Update the transformation prompt to add 'preserve all distinctive facial features, skin tone, hair texture, and hair color from the reference image exactly as they appear' as the first instruction."

---

### Issue: "Deployment fails with a permission error"

**Cause:** Cloud Run API not enabled or insufficient IAM permissions
**Solution:** In Google Cloud Console, go to APIs & Services and enable the Cloud Run API. Verify your account has the Cloud Run Admin role under IAM & Admin.

---

### Issue: "Can't find the Publish button"

**Cause:** App may not have built successfully
**Solution:** Check the Code tab for error indicators. Try refreshing the page. The Publish button appears in the top-right area once the app generates without errors.

---

### Issue: "App works in Preview but fails when published"

**Cause:** API key not properly transferred to Cloud Run
**Solution:** Go to Google Cloud Console → Cloud Run → your service → "Edit & Deploy New Revision" → Variables & Secrets tab. Verify that `GEMINI_API_KEY` (or similar) is present as an environment variable. If missing, republish from Build mode.

---

### Issue: "Transformations are slow (over 30 seconds)"

**Cause:** Large image files or high API load during peak hours
**Solution:** Tell the agent: "Add automatic image compression to reduce file size to under 1MB before sending to the API." Also add a user-facing message: "Processing may take 20 to 30 seconds for best results."

---

## Upgrading to Nano Banana 2 or Nano Banana Pro

Once you're comfortable with the workflow, you may want to upgrade the image model for better results:

**Nano Banana 2** (gemini-3.1-flash-image-preview): Released February 2026, built on Gemini 3.1 Flash. Faster generation (4 to 6 seconds at 1K), supports up to 4K resolution, better text rendering, and Image Search Grounding. Costs approximately $0.067 per image at 1K. No free API tier.

**Nano Banana Pro** (gemini-3-pro-image-preview): Built on Gemini 3 Pro. Highest image quality, best for final production assets with precise text. Costs approximately $0.134 per image at 1K. No free API tier.

**How to upgrade:** In Build mode, tell the agent: "Change the model from gemini-2.5-flash-image to gemini-3.1-flash-image-preview for better image quality." Test in Preview, then republish. Note that upgrading moves you off the free tier, so budget alerts become more important.

For this tutorial, the original Nano Banana is the right starting point because it lets you build, test, and iterate without spending anything.

---

## Your Turn: Try These Projects

The pattern you learned today works for any application: identify a problem, describe a solution, let AI build it, test with real users, publish. Here are five projects that build on the same skills, ordered from most similar to the headshot generator to most different. Each one includes a copy-paste-ready prompt so you can go straight to Build mode and start.

---

### Project 1: Product Photo Enhancer

**What it does:** Transforms amateur product photos into professional e-commerce images with clean backgrounds, consistent lighting, and enhanced colors.

**App description to use:**

```
Build an e-commerce product photo enhancer. Users upload product photos (JPG, PNG) through a clean drag-and-drop interface. Use Nano Banana (gemini-2.5-flash-image) to transform the uploaded product photo using this prompt:

"Transform this product photo into a professional e-commerce listing image. Place the product on a clean, pure white background with soft, even studio lighting. Enhance colors to be vibrant but accurate. Remove any background clutter. Add a subtle shadow beneath the product for depth. The result should look like a professional product photography studio shot, suitable for Amazon, Etsy, or Shopify listings. Preserve all product details, textures, and proportions exactly."

Include side-by-side before/after comparison, download button, and an option to choose between white background, lifestyle background, or gradient background. Mobile responsive design.
```

**Why this matters:** E-commerce sellers pay $5 to $20 per product photo. A seller with 50 products spends $250 to $1,000 just on photography. An app that does this for free has immediate commercial value.

**Skills you'll practice:** Same Nano Banana image transformation workflow, but with a different prompt structure. Teaches you that the transformation prompt is the key variable; the rest of the app architecture stays the same.

---

### Project 2: Real Estate Photo Stager

**What it does:** Takes photos of empty rooms and virtually stages them with furniture, decor, and styling based on the user's selected design preference.

**App description to use:**

```
Build a virtual staging app for real estate. Users upload photos of empty or unfurnished rooms. Use Nano Banana (gemini-2.5-flash-image) to transform the photos into professionally staged spaces.

Include a dropdown menu where users select a design style before transformation:
- Modern Minimalist (clean lines, neutral tones, simple furniture)
- Traditional (warm wood tones, classic furniture, area rugs)
- Coastal (light blues, whites, natural textures, beach inspired)

Use this transformation prompt (append the selected style):

"Transform this empty room photo into a professionally staged space in [SELECTED STYLE] style. Add appropriate furniture, decor, lighting fixtures, and accessories that match the room's dimensions and architecture. Keep the room's walls, floors, windows, and structural elements exactly as they appear. The staging should look photorealistic, as if a professional interior designer furnished the space. Ensure furniture is properly scaled and placed logically within the room."

Include before/after slider comparison, download button, and the ability to try different styles on the same room photo without re-uploading.
```

**Why this matters:** Professional staging costs $300 to $600 per property, and virtual staging services charge $25 to $75 per photo. Real estate agents who stage homes sell them 73% faster on average. An app that does this for free is genuinely useful.

**Skills you'll practice:** Adding user input (dropdown menu) that modifies the AI prompt dynamically. This is a step up from the headshot generator because the transformation isn't fixed; it changes based on user selection.

---

### Project 3: Resume Reviewer with AI Feedback

**What it does:** Analyzes an uploaded resume and provides specific, actionable improvement suggestions for impact, clarity, and ATS (Applicant Tracking System) optimization.

**App description to use:**

```
Create a resume analysis app. Users upload their resume as a PDF. Use Gemini to analyze the document and provide structured feedback in these categories:

1. IMPACT: Are accomplishments quantified? Are action verbs strong? Suggest specific rewrites for weak bullet points.
2. CLARITY: Is the formatting consistent? Are there grammar or spelling issues? Is the layout ATS-friendly?
3. ATS OPTIMIZATION: Identify missing keywords based on common job posting language. Flag formatting that ATS systems struggle to parse (tables, columns, graphics).
4. OVERALL SCORE: Rate the resume 1-10 with a brief justification.

Display results in a clean, tabbed interface with each category in its own section. Use color coding: green for strengths, yellow for suggestions, red for critical issues. Include a "Generate Improved Version" button that rewrites the resume content with the suggested improvements applied.
```

**Why this matters:** This project uses Gemini's text analysis capabilities instead of image generation. It teaches you that Build mode isn't limited to image apps; any Gemini capability (text, vision, documents) can be the backbone of your application. Resume review services charge $100 to $300 per session.

**Skills you'll practice:** Working with PDF document input instead of images. Displaying structured AI output in a tabbed interface. This is your first non-image Build mode project.

---

### Project 4: Social Media Caption Generator

**What it does:** Users upload an image and select a social media platform. Gemini analyzes the image and generates platform-optimized captions with relevant hashtags.

**App description to use:**

```
Create a social media caption generator. Users upload an image and select a target platform from a dropdown: Instagram, LinkedIn, or Twitter/X.

Use Gemini to analyze the uploaded image and generate 3 caption variants optimized for the selected platform:

- Instagram: Conversational tone, emoji usage, 20-30 relevant hashtags, engagement question at the end
- LinkedIn: Professional tone, industry insight angle, 3-5 strategic hashtags, call-to-action for comments
- Twitter/X: Concise (under 280 characters), witty or insightful, 2-3 hashtags maximum, designed for retweets

Display all three variants in card format. Each card has a "Copy to Clipboard" button. Include a "Regenerate" button that produces 3 new variants without re-uploading the image. Clean, modern UI with the uploaded image displayed prominently at the top.
```

**Why this matters:** Combines vision AI (understanding what's in the image) with text generation (writing platform-specific copy). Content creators and social media managers spend 30 to 60 minutes per post crafting captions. This reduces that to seconds.

**Skills you'll practice:** Multi-output generation (3 variants per request). Copy-to-clipboard functionality. Platform-specific prompt engineering. This teaches you that the same AI can produce very different outputs depending on the instructions.

---

### Project 5: Voice-to-Task Manager

**What it does:** Users speak tasks aloud, and the app extracts the task name, date, time, and priority, then displays organized task cards.

**App description to use:**

```
Build a voice-controlled task manager. Users click a microphone button to speak tasks like "Add dentist appointment tomorrow at 2pm, high priority" or "Remind me to buy groceries on Saturday."

Use Gemini with the Live API for voice input. The AI should extract:
- Task name
- Date (convert relative dates like "tomorrow" to actual dates)
- Time (if mentioned)
- Priority level (high, medium, low - default to medium if not stated)

Display tasks as cards grouped by date, with color-coded priority borders (red for high, yellow for medium, green for low). Include edit and delete buttons on each card. Add a text input field as a fallback for users who prefer typing. Store tasks in the browser session so they persist until the page is closed.
```

**Why this matters:** This is the most complex project in this list. It introduces voice interaction through the Live API, structured data extraction from natural language, and dynamic UI that updates as tasks are added. These are the building blocks of conversational AI applications, which are increasingly relevant in workplace automation.

**Skills you'll practice:** Working with the Live API for audio input. Parsing structured data from unstructured speech. Building dynamic, stateful interfaces. This project stretches your Build mode skills significantly beyond image transformation.

---

### The Pattern Behind All Five Projects

Every project above follows the same workflow you used for your headshot generator:

1. **Identify a problem** people actually have
2. **Describe the solution** clearly and specifically in the Build mode prompt
3. **Let the Antigravity agent** generate the implementation
4. **Test thoroughly** in the Preview panel with realistic inputs
5. **Iterate** based on what you see
6. **Publish** to Cloud Run and share
7. **Gather feedback** and improve

The prompts get more complex as you move from Project 1 to Project 5, but the workflow stays identical. That's the power of vibe coding: the process scales while the skill requirement stays constant.

---

## Additional Resources

**Official Documentation:**
- Google AI Studio: https://aistudio.google.com
- Build Mode Documentation: https://ai.google.dev/gemini-api/docs/aistudio-build-mode
- Nano Banana (Image Generation): https://ai.google.dev/gemini-api/docs/image-generation
- Gemini API Pricing: https://ai.google.dev/gemini-api/docs/pricing
- Cloud Run Pricing: https://cloud.google.com/run/pricing
- Deploy from AI Studio Codelab: https://codelabs.developers.google.com/deploy-from-aistudio-to-run

**Learning Resources:**
- AI Studio YouTube Playlist: https://www.youtube.com/playlist?list=PLOU2XLYxmsIKkEa_-KTPF9DZ0IyHJ7V1H
- Nano Banana Prompting Guide: https://cloud.google.com/blog/products/ai-machine-learning/ultimate-prompting-guide-for-nano-banana
- App Gallery for Inspiration: https://aistudio.google.com/apps?source=showcase

---

## Success Checklist

**Setup:**
- [ ] Created Google AI Studio account
- [ ] Opened Build mode and selected the Image Generation AI Chip
- [ ] Set up a Google Cloud project with billing enabled (for deployment only)

**Building:**
- [ ] Wrote a comprehensive app description specifying Nano Banana (gemini-2.5-flash-image)
- [ ] Generated the app with the Antigravity agent
- [ ] Tested transformations in the Preview panel with multiple photos
- [ ] Refined the UI using the chat panel or Annotation Mode

**Deployment:**
- [ ] Successfully published to Cloud Run
- [ ] Tested the live URL in an incognito browser window
- [ ] Verified mobile responsiveness
- [ ] Set up a budget alert in Google Cloud Console

**Sharing:**
- [ ] Shared the URL with at least 5 people
- [ ] Gathered specific feedback on transformation quality
- [ ] Made at least one improvement based on real usage

---

— Carlos Marquez, Professor of Applied AI and Data Analytics, Miami Dade College
