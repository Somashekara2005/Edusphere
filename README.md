# Edusphere

Edusphere is a full-stack educational web application that uses APIs to generate study roadmaps, free study resources, and quizzes. Rather than relying solely on static course material, its architecture centers on turning a learner's chosen topic into a structured learning path, supporting reference material, and interactive knowledge checks.

## Theoretical Architecture & Design

Edusphere follows a client-server full-stack separation between a user-facing web interface and a Python/Flask backend service layer:

- **Separation of Presentation and Generation Logic:** The frontend (`src/`, `public/`, `build/`) manages user interaction, navigation across learning workflows, and presentation state, while the backend (`backend/`) encapsulates API integration and content-generation logic[cite: 1].
- **Workflow-Driven Learning Loop:** The module layout reflects a step-by-step learning cycle—starting from topic selection (`input`), moving into structured progression (`roadmap`) and supporting study materials (`generativeResources`), reinforcing retention through assessment (`quiz`), and tracking learner context (`profile`) alongside language support (`translate`)[cite: 1].
- **API-Mediated Content Generation:** Instead of hardcoding every subject's curriculum, the backend is structured around specialized Python modules (`roadmap.py`, `generativeResources.py`, `quiz.py`) coordinated through a base application setup (`base.py`) to produce dynamic learning outputs via external APIs[cite: 1].

## Core Modules & Functional Roles

### Backend (`backend/`)

- **`base.py`:** Serves as the core Flask application foundation, wiring together backend routes, application configuration, and request handling[cite: 1].
- **`roadmap.py`:** Handles the theoretical structuring of a topic into an ordered study sequence or learning milestones so learners can approach unfamiliar subjects systematically[cite: 1].
- **`generativeResources.py`:** Focuses on sourcing or generating free study materials aligned with what a learner needs to study, complementing the roadmap with reference material[cite: 1].
- **`quiz.py`:** Supports active recall and comprehension testing by generating or managing quiz questions tied to the learning topic[cite: 1].
- **`.env` & `.flaskenv`:** Hold environment configuration and Flask runtime settings (such as API credentials and environment flags) outside source code[cite: 1].
- **`requirements.txt`:** Declares the Python package dependencies required to run the Flask backend[cite: 1].

### Frontend (`src/`, `public/`, `build/`)

- **Pages (`src/pages/`):**
  - **`input/` (`topic.js`, `topic.css`):** Captures the learner's topic input and initiates the roadmap and resource workflow[cite: 1].
  - **`roadmap/` (`roadmap.js`, `roadmap.css`):** Presents the generated study roadmap and guides the learner through planned steps[cite: 1].
  - **`quiz/` (`quiz.js`, `quiz.css`):** Provides the interactive interface for taking quizzes and evaluating understanding[cite: 1].
  - **`profile/` (`profile.js`, `profile.css`):** Represents user-specific profile information and personal learning context[cite: 1].
- **Components (`src/components/`):**
  - **`header/` (`header.js`, `header.css`):** Provides top-level navigation and persistent header UI[cite: 1].
  - **`loader/` (`loader.js`, `loader.css`):** Displays loading states while asynchronous API requests (such as roadmap, resource, or quiz generation) are in progress[cite: 1].
  - **`modal/` (`modal.js`, `modal.css`):** Handles focused overlay dialogs or prompts within the interface[cite: 1].
- **Translation (`src/translate/translate.js`):** Supports language translation functionality across learning content or UI text[cite: 1].
- **Entry & Styling (`src/App.js`, `src/index.js`, `src/App.css`, `src/index.css`):** Initializes the client application, root component hierarchy, and global styles[cite: 1].
- **`public/` & `build/`:** `public/` contains static assets (`index.html`, `manifest.json`, `robots.txt`, and visual assets such as `logo.png`, `avatar.jpg`, `hackathon_banner.png`, `process_flow.png`, `image.png`, `image-1.png`, `image-2.png`), while `build/` holds compiled production assets[cite: 1].
- **`edu.mp4`:** A video file in the repository root illustrating or demonstrating the application[cite: 1].

## Repository Structure

```text
Edusphere-main/
├── backend/
│   ├── .env
│   ├── .flaskenv
│   ├── base.py
│   ├── generativeResources.py
│   ├── quiz.py
│   ├── requirements.txt
│   └── roadmap.py
├── build/
├── public/
├── src/
│   ├── components/
│   │   ├── header/
│   │   ├── loader/
│   │   └── modal/
│   ├── pages/
│   │   ├── input/
│   │   ├── profile/
│   │   ├── quiz/
│   │   └── roadmap/
│   ├── translate/
│   ├── App.js
│   ├── App.css
│   ├── index.js
│   └── index.css
├── edu.mp4
├── package.json
├── package-lock.json
└── README.md
