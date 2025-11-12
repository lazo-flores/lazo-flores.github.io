# Jose Lazo-Flores, Ph.D. - Personal Website

Personal website showcasing my professional journey, expertise in data science and AI, and portfolio of agentic AI projects.

## Overview

This website serves as a comprehensive portfolio and professional profile, featuring:
- Professional background and experience
- AI and data science project showcase
- Interactive AI twin for visitor engagement
- Direct contact information and CV download

**Live Site:** https://lazo-flores.github.io

## Technology Stack

- **Template:** Tessellate by HTML5 UP
- **Frontend:** HTML5, CSS3, JavaScript
- **Responsive Design:** Mobile-first approach with breakpoints
- **Embedded Apps:** HuggingFace Spaces integration

## Structure

### Navigation Bar
Fixed navigation bar at the top of the page with smooth scrolling:
- Home
- About Me
- Experience
- Projects
- AI Twin
- Contact

**Location:** Lines 191-204 in `index.html`

**Styling:** Lines 15-103 in `<style>` block
- Fixed positioning with semi-transparent dark background
- Responsive design for mobile/tablet
- Hover effects on navigation links

### Sections

#### 1. Header Section
- Name and professional title
- Profile image (OfficeBackgroundMe.png)
- Call-to-action button

**Location:** Lines 206-223 in `index.html`

#### 2. About Me Section
- Professional bio highlighting physics background and data science expertise
- Three skill areas presented in columns:
  - Data Science & AI
  - Data Engineering
  - Analytics & Research

**Location:** Lines 225-269 in `index.html`

#### 3. Professional Experience Section
- Detailed work history (2015-2024)
- Research experience at CERN, Fermilab, PSI
- Education (Ph.D. in Physics, B.S. in Engineering Physics)
- Download CV button

**Location:** Lines 271-339 in `index.html`

**CV File:** `documents/Lazo-Flores_Jose_CV V10.3.pdf`

#### 4. AI Projects Section
Four featured projects with:
- Project images (uniform 300px height, responsive)
- Detailed descriptions
- Technology tags (styled as badges)
- Live Demo and View Code buttons

**Projects:**
1. **AI Instructor Assistant**
   - Image: `images/InstructorAssistant.png`
   - Demo: https://huggingface.co/spaces/jlazoflores/instructor_assistant
   - Code: https://github.com/lazo-flores/instructor_assistant

2. **Deep Research Agent**
   - Image: `images/DeepResearch.jpg`
   - Demo: https://huggingface.co/spaces/jlazoflores/deep_research
   - Code: https://github.com/lazo-flores/deep_research

3. **Financial Advisor and Agent Dashboard**
   - Image: `images/FinancialAdvisor.jpg`
   - Demo: Coming Soon (button disabled)
   - Code: https://github.com/lazo-flores/trading_floor

4. **Document Proofreader Agent**
   - Image: `images/ProofReader.png`
   - Demo: https://0758b91d9bab673c2a.gradio.live
   - Code: https://github.com/lazo-flores/proof_reader

**Location:** Lines 341-475 in `index.html`

#### 5. AI Twin Section
Interactive embedded application allowing visitors to chat with an AI agent trained on professional background and expertise.

**Location:** Lines 640-660 in `index.html`

**Embedded App:** https://jlazoflores-twin-agent.hf.space

**Features:**
- HuggingFace Spaces iframe integration
- Responsive design (850px desktop, 100% width mobile)
- Styled with rounded corners and shadow

#### 6. Contact Section
- Email contact information
- Links to LinkedIn and GitHub in footer
- Social media icons

**Location:** Lines 662-689 in `index.html`

## Custom Styling

### Technology Tags
Visual badges for technologies used in each project.

**CSS Location:** Lines 120-138 in `<style>` block

**Features:**
- Orange/gold color scheme
- Semi-transparent background
- Flexbox layout for wrapping
- Border and padding for visual separation

### Project Images
Uniform sizing for all project screenshots.

**CSS Location:** Lines 104-118 in `<style>` block

**Features:**
- Fixed 300px height on desktop, 250px on mobile
- `object-fit: cover` for consistent cropping
- Rounded corners (8px)
- Bottom margin for spacing

### Project Buttons
Centered Live Demo and View Code buttons.

**Features:**
- Centered using flexbox with `justify-content: center`
- Gap between buttons
- Wrapping on small screens
- Disabled state styling for unavailable demos

**Disabled Button CSS:** Lines 159-165

### Responsive Design
Mobile-first approach with breakpoints:
- **736px:** Tablet adjustments
- **480px:** Mobile phone adjustments

Navigation stacks vertically on mobile, images scale responsively, and iframe adjusts to full width.

## File Structure

```
lazo-flores.github.io/
├── index.html              # Main website file
├── README.md               # This documentation
├── assets/
│   ├── css/               # Stylesheets
│   ├── js/                # JavaScript files
│   ├── sass/              # SASS source files
│   └── webfonts/          # Icon fonts
├── images/
│   ├── OfficeBackgroundMe.png      # Profile photo
│   ├── InstructorAssistant.png     # Project 1 image
│   ├── DeepResearch.jpg            # Project 2 image
│   ├── FinancialAdvisor.jpg        # Project 3 image
│   ├── ProofReader.png             # Project 4 image
│   └── [other template images]
├── documents/
│   └── Lazo-Flores_Jose_CV V10.3.pdf  # CV for download
└── WebsiteIntroInfo.txt    # Source content file
```

## Local Development

### Running Local Server

```bash
# Navigate to project directory
cd lazo-flores.github.io

# Start Python HTTP server
python3 -m http.server 8000

# Open browser to http://localhost:8000
```

### Stopping the Server

Press `Ctrl+C` in the terminal where the server is running.

## Updating Content

### Updating Project Links

To update project demo or repository links:

1. Locate the project section in `index.html` (lines 341-475)
2. Find the button anchor tags
3. Update the `href` attribute

**Example:**
```html
<a href="YOUR_DEMO_URL" class="button" target="_blank">Live Demo</a>
<a href="YOUR_REPO_URL" class="button" target="_blank">View Code</a>
```

### Enabling Disabled Buttons

To enable the Financial Advisor demo button when ready:

1. Locate line 414 in `index.html`
2. Remove the `disabled` class
3. Change text from "Live Demo (Coming Soon)" to "Live Demo"
4. Add `target="_blank"` attribute
5. Update the `href` to your demo URL

**Before:**
```html
<a href="#" class="button disabled">Live Demo (Coming Soon)</a>
```

**After:**
```html
<a href="YOUR_DEMO_URL" class="button" target="_blank">Live Demo</a>
```

### Updating CV

Replace the PDF file in the `documents/` folder with the same filename, or update the link at line 256 in `index.html`:

```html
<a href="documents/YOUR_CV_FILENAME.pdf" class="button" download>Download CV</a>
```

### Updating Profile Image

Replace `images/OfficeBackgroundMe.png` with your new image (same filename), or update line 219 in `index.html`:

```html
<img src="images/YOUR_IMAGE.png" alt="Jose Lazo-Flores" style="border-radius: 10px;" />
```

### Updating Project Images

Replace image files in the `images/` folder or update the respective `<img>` tags (lines 328, 357, 383, 412).

## Deployment

### GitHub Pages Setup

This repository is configured for GitHub Pages deployment:

1. Push changes to the `main` branch
2. GitHub Pages will automatically build and deploy
3. Site will be available at https://lazo-flores.github.io

### Manual Deployment

If deploying elsewhere:
1. Upload all files to your web server
2. Ensure the root directory contains `index.html`
3. Set appropriate permissions for web serving

## Credits

- **Template:** [Tessellate by HTML5 UP](http://html5up.net)
- **License:** CCA 3.0 License (html5up.net/license)
- **Icons:** Font Awesome
- **Fonts:** Roboto (Google Fonts)

## Contact

**Jose Lazo-Flores, Ph.D.**
- Email: Jose.Lazo.Flores.1@gmail.com
- GitHub: https://github.com/lazo-flores
- LinkedIn: https://www.linkedin.com/in/jose-lazo-flores-52b21a82/
