# React + Storybook UI Component Library

This project is a comprehensive UI component library built with React, TypeScript, styled-components, and Storybook. It provides a collection of reusable, responsive, and accessible components that can be used across different projects.

## 📦 Getting Started

### Prerequisites

- Node.js 20 or higher
- Docker and Docker Compose

### Local Development

1. **Clone the repository**
   ```bash
   git clone https://github.com/senli-rrc/li_jason_coding_assignment12.git
   cd li_jason_coding_assignment12
   ```

2. **Install dependencies**
   ```bash
   cd li_jason_ui_garden
   npm install --legacy-peer-deps
   ```

3. **Run Storybook locally**
   ```bash
   npm run storybook
   ```
   This will start Storybook on `http://localhost:8083`

4. **Run tests**
   ```bash
   npm run test
   ```

### 🐳 Docker Compose Development

For local development with Docker Compose (includes hot reload):

1. **Start the development environment**
   ```bash
   docker-compose -f docker-compose.dev.yml up
   ```
   This will:
   - Build the development Docker image
   - Start Storybook with hot reload
   - Mount your local source code for live editing
   - Make Storybook available at `http://localhost:8083`

2. **Stop the development environment**
   ```bash
   docker-compose -f docker-compose.dev.yml down
   ```

3. **Rebuild after dependency changes**
   ```bash
   docker-compose -f docker-compose.dev.yml up --build
   ```
4. **Build a production**
   ```bash
   docker build -t li_jason_coding_assignment12 .
   ```

5. **Run the Image**
   ```bash
   docker run -p 8083:8083 li_jason_coding_assignment12
   ```