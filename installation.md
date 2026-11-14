---
layout: doc
title: Installation Guide
description: Learn how to set up your Jekyll documentation site locally or via GitHub Pages.
---

## Overview {#overview}
Welcome to the installation guide. Follow these steps to get your documentation site running locally on your machine or deployed via GitHub Pages.

## Prerequisites {#prerequisites}
Before getting started, make sure you have the following installed on your system:
- **Ruby** and **Bundler** (required for Jekyll)
- **Node.js** and **npm** (required for Tailwind CSS)

## Step-by-Step Setup {#setup}
Open your terminal and run the following commands to create and initialize your new Jekyll documentation project:

```bash
# 1. Install Jekyll and Bundler gems
gem install jekyll bundler

# 2. Create a new Jekyll site in your workspace
jekyll new my-docs-site
cd my-docs-site

# 3. Serve the site locally
bundle exec jekyll serve