<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tailwind CSS Style Docs & Jekyll Template</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        sky: {
                            500: '#06b6d4',
                            600: '#0891b2',
                            400: '#38bdf8',
                        }
                    }
                }
            }
        }
    </script>
    <!-- Inter Font -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=Fira+Code:wght@400;500&display=swap" rel="stylesheet">
    <!-- FontAwesome for Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        body {
            font-family: 'Inter', sans-serif;
        }
        code, pre {
            font-family: 'Fira Code', monospace;
        }
        /* Custom scrollbar for doc sidebar */
        ::-webkit-scrollbar {
            width: 5px;
            height: 5px;
        }
        ::-webkit-scrollbar-track {
            background: transparent;
        }
        ::-webkit-scrollbar-thumb {
            background: #cbd5e1;
            border-radius: 9999px;
        }
        .dark ::-webkit-scrollbar-thumb {
            background: #334155;
        }
    </style>
</head>
<body class="bg-white text-slate-700 dark:bg-slate-900 dark:text-slate-300 transition-colors duration-200">

    <!-- Top Sticky Header Navigation -->
    <header class="sticky top-0 z-40 w-full backdrop-blur flex-none transition-colors duration-500 lg:z-50 lg:border-b lg:border-slate-900/10 dark:border-slate-50/[0.06] bg-white/95 dark:bg-slate-900/75 border-b border-slate-200">
        <div class="max-w-8xl mx-auto">
            <div class="py-3 px-4 lg:px-8 flex items-center justify-between">
                <!-- Brand / Logo -->
                <div class="flex items-center gap-4">
                    <button id="mobile-menu-btn" class="lg:hidden text-slate-500 hover:text-slate-600 dark:hover:text-slate-300 focus:outline-none">
                        <i class="fa-solid fa-bars text-xl"></i>
                    </button>
                    <a href="#" class="flex items-center gap-2 text-slate-900 dark:text-white font-bold text-lg tracking-tight">
                        <svg class="h-6 w-auto fill-sky-500" viewBox="0 0 24 24">
                            <path d="M12.001 4.8c-3.2 0-5.2 1.6-6 4.8 1.2-1.6 2.6-2.2 4.2-1.8.913.228 1.565.89 2.288 1.624C13.666 10.618 15.027 12 18.001 12c3.2 0 5.2-1.6 6-4.8-1.2 1.6-2.6 2.2-4.2 1.8-.913-.228-1.565-.89-2.288-1.624C16.336 6.182 14.975 4.8 12.001 4.8zm-6 7.2c-3.2 0-5.2 1.6-6 4.8 1.2-1.6 2.6-2.2 4.2-1.8.913.228 1.565.89 2.288 1.624C3.666 17.818 5.027 19.2 8.001 19.2c3.2 0 5.2-1.6 6-4.8-1.2 1.6-2.6 2.2-4.2 1.8-.913-.228-1.565-.89-2.288-1.624C6.336 13.382 4.975 12 2.001 12z"/>
                        </svg>
                        <span>JekyllDocs</span>
                        <span class="text-xs bg-sky-500/10 text-sky-500 dark:text-sky-400 font-semibold px-2 py-0.5 rounded-full">v3.4.0</span>
                    </a>
                </div>

                <!-- Global Search Box -->
                <div class="hidden md:flex flex-1 max-w-md mx-8">
                    <div class="relative w-full">
                        <span class="absolute inset-y-0 left-0 flex items-center pl-3 pointer-events-none text-slate-400">
                            <i class="fa-solid fa-magnifying-glass text-sm"></i>
                        </span>
                        <input type="text" id="doc-search-input" placeholder="Quick search... (Press '/' to focus)" class="w-full pl-9 pr-12 py-1.5 text-sm rounded-lg bg-slate-100 dark:bg-slate-800 text-slate-800 dark:text-slate-200 border border-transparent focus:border-sky-500 focus:bg-white dark:focus:bg-slate-900 focus:outline-none transition-all placeholder-slate-400">
                        <span class="absolute inset-y-0 right-0 flex items-center pr-3 pointer-events-none text-xs text-slate-400">
                            <kbd class="px-1.5 py-0.5 border border-slate-300 dark:border-slate-700 rounded shadow-xs bg-slate-50 dark:bg-slate-800">⌘K</kbd>
                        </span>
                    </div>
                </div>

                <!-- Right Utilities -->
                <div class="flex items-center gap-4">
                    <!-- Tab Selector (Preview vs Jekyll Source) -->
                    <div class="flex items-center bg-slate-100 dark:bg-slate-800 p-1 rounded-lg text-xs font-semibold">
                        <button id="tab-btn-docs" onclick="switchView('docs')" class="px-3 py-1 rounded-md bg-white dark:bg-slate-700 text-sky-600 dark:text-sky-400 shadow-sm transition">Docs Preview</button>
                        <button id="tab-btn-jekyll" onclick="switchView('jekyll')" class="px-3 py-1 rounded-md text-slate-600 dark:text-slate-400 hover:text-slate-900 dark:hover:text-white transition">Jekyll Code Template</button>
                    </div>

                    <!-- Theme Toggle -->
                    <button id="theme-toggle" title="Toggle Light/Dark Theme" class="p-2 rounded-lg text-slate-500 hover:text-slate-700 dark:text-slate-400 dark:hover:text-white focus:outline-none">
                        <i id="theme-toggle-dark-icon" class="fa-solid fa-moon text-lg hidden"></i>
                        <i id="theme-toggle-light-icon" class="fa-solid fa-sun text-lg hidden"></i>
                    </button>

                    <!-- GitHub Link -->
                    <a href="https://github.com" target="_blank" class="text-slate-400 hover:text-slate-500 dark:hover:text-slate-300">
                        <i class="fa-brands fa-github text-xl"></i>
                    </a>
                </div>
            </div>
        </div>
    </header>

    <!-- Mobile Drawer Overlay -->
    <div id="mobile-sidebar-backdrop" class="fixed inset-0 z-40 bg-slate-900/50 backdrop-blur-sm hidden lg:hidden"></div>

    <!-- MAIN CONTAINER -->
    <div class="max-w-8xl mx-auto px-4 sm:px-6 lg:px-8">
        
        <!-- ================= VIEW 1: LIVE DOCUMENTATION SHOWCASE ================= -->
        <div id="docs-view" class="flex min-h-[calc(100vh-4rem)]">
            
            <!-- Left Sidebar Navigation -->
            <aside id="sidebar" class="fixed inset-y-0 left-0 z-50 w-64 bg-white dark:bg-slate-900 border-r border-slate-200 dark:border-slate-800 transform -translate-x-full lg:translate-x-0 lg:static lg:z-auto transition-transform duration-300 ease-in-out overflow-y-auto pt-20 lg:pt-8 pb-10 px-6">
                <nav class="space-y-8 text-sm">
                    <div>
                        <h3 class="font-semibold text-slate-900 dark:text-white uppercase tracking-wider text-xs mb-3">Getting Started</h3>
                        <ul class="space-y-2 border-l border-slate-200 dark:border-slate-800 pl-3">
                            <li><a href="#overview" class="doc-nav-link text-sky-600 dark:text-sky-400 font-medium border-l-2 -ml-[13px] pl-3 border-sky-500 block">Overview & Setup</a></li>
                            <li><a href="#installation" class="doc-nav-link text-slate-600 dark:text-slate-400 hover:text-slate-900 dark:hover:text-white block">Installation Guide</a></li>
                            <li><a href="#configuration" class="doc-nav-link text-slate-600 dark:text-slate-400 hover:text-slate-900 dark:hover:text-white block">Configuration Settings</a></li>
                        </ul>
                    </div>

                    <div>
                        <h3 class="font-semibold text-slate-900 dark:text-white uppercase tracking-wider text-xs mb-3">Core Components</h3>
                        <ul class="space-y-2 border-l border-slate-200 dark:border-slate-800 pl-3">
                            <li><a href="#typography" class="doc-nav-link text-slate-600 dark:text-slate-400 hover:text-slate-900 dark:hover:text-white block">Typography & Content</a></li>
                            <li><a href="#code-blocks" class="doc-nav-link text-slate-600 dark:text-slate-400 hover:text-slate-900 dark:hover:text-white block">Code Blocks & Syntax</a></li>
                            <li><a href="#callouts" class="doc-nav-link text-slate-600 dark:text-slate-400 hover:text-slate-900 dark:hover:text-white block">Callouts & Alerts</a></li>
                            <li><a href="#tables" class="doc-nav-link text-slate-600 dark:text-slate-400 hover:text-slate-900 dark:hover:text-white block">Data Tables</a></li>
                        </ul>
                    </div>

                    <div>
                        <h3 class="font-semibold text-slate-900 dark:text-white uppercase tracking-wider text-xs mb-3">Customization</h3>
                        <ul class="space-y-2 border-l border-slate-200 dark:border-slate-800 pl-3">
                            <li><a href="#theming" class="doc-nav-link text-slate-600 dark:text-slate-400 hover:text-slate-900 dark:hover:text-white block">Color Palettes & Dark Mode</a></li>
                            <li><a href="#jekyll-integration" class="doc-nav-link text-slate-600 dark:text-slate-400 hover:text-slate-900 dark:hover:text-white block">Jekyll Integration</a></li>
                        </ul>
                    </div>
                </nav>
            </aside>

            <!-- Main Content Area -->
            <main class="flex-1 min-w-0 py-8 lg:px-12">
                <!-- Page Title Header -->
                <div class="border-b border-slate-200 dark:border-slate-800 pb-6 mb-8">
                    <p class="text-sm font-semibold text-sky-500 uppercase tracking-wide">Documentation</p>
                    <h1 class="text-3xl sm:text-4xl font-extrabold text-slate-900 dark:text-white tracking-tight mt-1">Tailwind-Style Documentation Template</h1>
                    <p class="text-lg text-slate-600 dark:text-slate-400 mt-2">A sleek, modern responsive documentation layout optimized for Jekyll static site generation.</p>
                </div>

                <!-- SECTION 1: OVERVIEW -->
                <section id="overview" class="mb-12 scroll-mt-24">
                    <h2 class="text-2xl font-bold text-slate-900 dark:text-white tracking-tight mb-4">Overview & Setup</h2>
                    <p class="text-slate-600 dark:text-slate-400 leading-relaxed mb-4">
                        This template delivers a pixel-perfect documentation design modeled directly after modern frameworks like Tailwind CSS, Vite, and Next.js. Built with flexbox layouts, a sticky top navbar, collapsible mobile drawers, dynamic code highlighting styles, and automatic dark theme support.
                    </p>
                    
                    <!-- Feature Grid -->
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4 my-6">
                        <div class="p-4 rounded-xl bg-slate-50 dark:bg-slate-800/50 border border-slate-200 dark:border-slate-800">
                            <div class="w-8 h-8 rounded-lg bg-sky-500/10 text-sky-500 flex items-center justify-center mb-3">
                                <i class="fa-solid fa-mobile-screen"></i>
                            </div>
                            <h3 class="font-semibold text-slate-900 dark:text-white mb-1">Fully Responsive</h3>
                            <p class="text-sm text-slate-600 dark:text-slate-400">Mobile slide-over menu drawer with seamless touch targets and smooth overlay transitions.</p>
                        </div>

                        <div class="p-4 rounded-xl bg-slate-50 dark:bg-slate-800/50 border border-slate-200 dark:border-slate-800">
                            <div class="w-8 h-8 rounded-lg bg-sky-500/10 text-sky-500 flex items-center justify-center mb-3">
                                <i class="fa-solid fa-moon"></i>
                            </div>
                            <h3 class="font-semibold text-slate-900 dark:text-white mb-1">Theme Aware</h3>
                            <p class="text-sm text-slate-600 dark:text-slate-400">Automatic system preference detection paired with a manual toggle stored in local storage.</p>
                        </div>
                    </div>
                </section>

                <!-- SECTION 2: INSTALLATION -->
                <section id="installation" class="mb-12 scroll-mt-24">
                    <h2 class="text-2xl font-bold text-slate-900 dark:text-white tracking-tight mb-4">Installation Guide</h2>
                    <p class="text-slate-600 dark:text-slate-400 mb-4">To get started with Jekyll and Tailwind CSS CLI in your local development workspace, run the commands below:</p>

                    <!-- Code Box with Copy Button -->
                    <div class="relative group my-4 rounded-xl overflow-hidden bg-slate-950 border border-slate-800 shadow-xl">
                        <div class="flex items-center justify-between px-4 py-2 bg-slate-900 border-b border-slate-800 text-xs text-slate-400 font-mono">
                            <span>terminal</span>
                            <button onclick="copyCode(this)" class="hover:text-white flex items-center gap-1 transition">
                                <i class="fa-regular fa-copy"></i> Copy
                            </button>
                        </div>
                        <pre class="p-4 text-sm text-slate-200 overflow-x-auto"><code><span class="text-slate-500"># Install dependencies & initialize Jekyll site</span>
gem install jekyll bundler
jekyll new my-docs-site
cd my-docs-site

<span class="text-slate-500"># Install Tailwind CSS CLI</span>
npm install -D tailwindcss
npx tailwindcss init</code></pre>
                    </div>
                </section>

                <!-- SECTION 3: CONFIGURATION -->
                <section id="configuration" class="mb-12 scroll-mt-24">
                    <h2 class="text-2xl font-bold text-slate-900 dark:text-white tracking-tight mb-4">Configuration Settings</h2>
                    <p class="text-slate-600 dark:text-slate-400 mb-4">Configure your <code class="px-1.5 py-0.5 rounded bg-slate-100 dark:bg-slate-800 text-sky-500 text-xs font-mono">tailwind.config.js</code> file to scan Jekyll files for Tailwind class names:</p>

                    <div class="relative group my-4 rounded-xl overflow-hidden bg-slate-950 border border-slate-800 shadow-xl">
                        <div class="flex items-center justify-between px-4 py-2 bg-slate-900 border-b border-slate-800 text-xs text-slate-400 font-mono">
                            <span>tailwind.config.js</span>
                            <button onclick="copyCode(this)" class="hover:text-white flex items-center gap-1 transition">
                                <i class="fa-regular fa-copy"></i> Copy
                            </button>
                        </div>
                        <pre class="p-4 text-sm text-slate-200 overflow-x-auto"><code>module.exports = {
  darkMode: 'class',
  content: [
    './_layouts/**/*.html',
    './_includes/**/*.html',
    './_posts/*.md',
    './*.html',
    './*.md',
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}</code></pre>
                    </div>
                </section>

                <!-- SECTION 4: TYPOGRAPHY -->
                <section id="typography" class="mb-12 scroll-mt-24">
                    <h2 class="text-2xl font-bold text-slate-900 dark:text-white tracking-tight mb-4">Typography & Content</h2>
                    <p class="text-slate-600 dark:text-slate-400 leading-relaxed mb-4">
                        Standard Markdown text elements are formatted with clean vertical rhythms. Paragraphs have high legibility using system font stacks centered on Inter.
                    </p>
                    <ul class="list-disc list-inside text-slate-600 dark:text-slate-400 space-y-2 mb-4">
                        <li>High contrast typography tailored for both dark and light mode themes.</li>
                        <li>Automated hover anchor icons next to headers.</li>
                        <li>Inline element formatting like <a href="#" class="text-sky-500 underline underline-offset-2 hover:text-sky-600">hyperlinks</a> and highlighted key points.</li>
                    </ul>
                </section>

                <!-- SECTION 5: CODE BLOCKS -->
                <section id="code-blocks" class="mb-12 scroll-mt-24">
                    <h2 class="text-2xl font-bold text-slate-900 dark:text-white tracking-tight mb-4">Code Blocks & Syntax</h2>
                    <p class="text-slate-600 dark:text-slate-400 mb-4">Example HTML snippet demonstrating built-in code formatting with copy triggers:</p>

                    <div class="relative group my-4 rounded-xl overflow-hidden bg-slate-950 border border-slate-800 shadow-xl">
                        <div class="flex items-center justify-between px-4 py-2 bg-slate-900 border-b border-slate-800 text-xs text-slate-400 font-mono">
                            <span>example.html</span>
                            <button onclick="copyCode(this)" class="hover:text-white flex items-center gap-1 transition">
                                <i class="fa-regular fa-copy"></i> Copy
                            </button>
                        </div>
                        <pre class="p-4 text-sm text-slate-200 overflow-x-auto"><code><span class="text-sky-400">&lt;div</span> <span class="text-purple-400">class</span>=<span class="text-emerald-300">"p-6 max-w-sm bg-white rounded-xl shadow-lg flex items-center space-x-4"</span><span class="text-sky-400">&gt;</span>
  <span class="text-sky-400">&lt;div</span> <span class="text-purple-400">class</span>=<span class="text-emerald-300">"shrink-0"</span><span class="text-sky-400">&gt;</span>
    <span class="text-sky-400">&lt;img</span> <span class="text-purple-400">class</span>=<span class="text-emerald-300">"h-12 w-12"</span> <span class="text-purple-400">src</span>=<span class="text-emerald-300">"/img/logo.svg"</span> <span class="text-purple-400">alt</span>=<span class="text-emerald-300">"Logo"</span><span class="text-sky-400">&gt;</span>
  <span class="text-sky-400">&lt;/div&gt;</span>
  <span class="text-sky-400">&lt;div&gt;</span>
    <span class="text-sky-400">&lt;div</span> <span class="text-purple-400">class</span>=<span class="text-emerald-300">"text-xl font-medium text-black"</span><span class="text-sky-400">&gt;</span>ChitChat<span class="text-sky-400">&lt;/div&gt;</span>
    <span class="text-sky-400">&lt;p</span> <span class="text-purple-400">class</span>=<span class="text-emerald-300">"text-slate-500"</span><span class="text-sky-400">&gt;</span>You have a new message!<span class="text-sky-400">&lt;/p&gt;</span>
  <span class="text-sky-400">&lt;/div&gt;</span>
<span class="text-sky-400">&lt;/div&gt;</span></code></pre>
                    </div>
                </section>

                <!-- SECTION 6: CALLOUTS -->
                <section id="callouts" class="mb-12 scroll-mt-24">
                    <h2 class="text-2xl font-bold text-slate-900 dark:text-white tracking-tight mb-4">Callouts & Alerts</h2>
                    
                    <!-- Info Callout -->
                    <div class="p-4 my-4 rounded-xl bg-sky-50 dark:bg-sky-950/40 border-l-4 border-sky-500 flex gap-3 text-sky-900 dark:text-sky-200">
                        <i class="fa-solid fa-circle-info text-sky-500 text-lg mt-0.5"></i>
                        <div class="text-sm">
                            <span class="font-semibold block mb-0.5">Pro Tip</span>
                            Use Jekyll's liquid tags to create reusable alert components across your markdown files.
                        </div>
                    </div>

                    <!-- Warning Callout -->
                    <div class="p-4 my-4 rounded-xl bg-amber-50 dark:bg-amber-950/40 border-l-4 border-amber-500 flex gap-3 text-amber-900 dark:text-amber-200">
                        <i class="fa-solid fa-triangle-exclamation text-amber-500 text-lg mt-0.5"></i>
                        <div class="text-sm">
                            <span class="font-semibold block mb-0.5">Warning</span>
                            Make sure Jekyll is configured to output compiled CSS files into the <code class="bg-amber-100 dark:bg-amber-900/50 px-1 rounded text-xs">/assets/css/</code> path.
                        </div>
                    </div>
                </section>

                <!-- SECTION 7: TABLES -->
                <section id="tables" class="mb-12 scroll-mt-24">
                    <h2 class="text-2xl font-bold text-slate-900 dark:text-white tracking-tight mb-4">Data Tables</h2>
                    <div class="overflow-x-auto rounded-xl border border-slate-200 dark:border-slate-800">
                        <table class="w-full text-left text-sm">
                            <thead class="bg-slate-50 dark:bg-slate-800/80 text-slate-900 dark:text-white font-semibold border-b border-slate-200 dark:border-slate-800">
                                <tr>
                                    <th class="p-3">Variable</th>
                                    <th class="p-3">Type</th>
                                    <th class="p-3">Default</th>
                                    <th class="p-3">Description</th>
                                </tr>
                            </thead>
                            <tbody class="divide-y divide-slate-200 dark:divide-slate-800">
                                <tr class="hover:bg-slate-50/50 dark:hover:bg-slate-800/30">
                                    <td class="p-3 font-mono text-xs text-sky-500">site.title</td>
                                    <td class="p-3 text-slate-500">String</td>
                                    <td class="p-3 text-slate-500 font-mono text-xs">"Docs Site"</td>
                                    <td class="p-3">Title of the site displayed in the navbar.</td>
                                </tr>
                                <tr class="hover:bg-slate-50/50 dark:hover:bg-slate-800/30">
                                    <td class="p-3 font-mono text-xs text-sky-500">page.toc</td>
                                    <td class="p-3 text-slate-500">Boolean</td>
                                    <td class="p-3 text-slate-500 font-mono text-xs">true</td>
                                    <td class="p-3">Toggles the right-side "On this page" sidebar.</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </section>

                <!-- SECTION 8: THEMING -->
                <section id="theming" class="mb-12 scroll-mt-24">
                    <h2 class="text-2xl font-bold text-slate-900 dark:text-white tracking-tight mb-4">Color Palettes & Dark Mode</h2>
                    <p class="text-slate-600 dark:text-slate-400 mb-4">This documentation layout natively responds to Tailwind's <code class="px-1.5 py-0.5 rounded bg-slate-100 dark:bg-slate-800 text-xs font-mono">dark</code> class selector on the HTML element.</p>
                </section>

                <!-- SECTION 9: JEKYLL INTEGRATION -->
                <section id="jekyll-integration" class="mb-12 scroll-mt-24">
                    <h2 class="text-2xl font-bold text-slate-900 dark:text-white tracking-tight mb-4">Jekyll Integration</h2>
                    <p class="text-slate-600 dark:text-slate-400 mb-4">Click the <strong>"Jekyll Code Template"</strong> tab in the header to view the full directory structure and file setup needed to turn this UI into a working Jekyll theme.</p>
                </section>

            </main>

            <!-- Right Sidebar ("On This Page") -->
            <aside class="hidden xl:block w-64 flex-none py-8 pl-8 text-xs">
                <div class="sticky top-24 space-y-3 border-l border-slate-200 dark:border-slate-800 pl-4">
                    <p class="font-semibold text-slate-900 dark:text-white uppercase tracking-wider">On this page</p>
                    <ul class="space-y-2.5 text-slate-500 dark:text-slate-400">
                        <li><a href="#overview" class="hover:text-sky-500 transition block">Overview & Setup</a></li>
                        <li><a href="#installation" class="hover:text-sky-500 transition block">Installation Guide</a></li>
                        <li><a href="#configuration" class="hover:text-sky-500 transition block">Configuration Settings</a></li>
                        <li><a href="#typography" class="hover:text-sky-500 transition block">Typography & Content</a></li>
                        <li><a href="#code-blocks" class="hover:text-sky-500 transition block">Code Blocks & Syntax</a></li>
                        <li><a href="#callouts" class="hover:text-sky-500 transition block">Callouts & Alerts</a></li>
                        <li><a href="#tables" class="hover:text-sky-500 transition block">Data Tables</a></li>
                        <li><a href="#theming" class="hover:text-sky-500 transition block">Color Palettes</a></li>
                        <li><a href="#jekyll-integration" class="hover:text-sky-500 transition block">Jekyll Integration</a></li>
                    </ul>
                </div>
            </aside>
        </div>

        <!-- ================= VIEW 2: JEKYLL SOURCE CODE TEMPLATES ================= -->
        <div id="jekyll-view" class="hidden py-8">
            <div class="max-w-4xl mx-auto space-y-8">
                <div>
                    <h1 class="text-3xl font-bold text-slate-900 dark:text-white mb-2">Jekyll Implementation Guide</h1>
                    <p class="text-slate-600 dark:text-slate-400">Below are the modular Jekyll templates and directory structure required to power this exact documentation design.</p>
                </div>

                <!-- Directory Structure Block -->
                <div class="rounded-xl bg-slate-950 p-6 border border-slate-800 text-slate-300 font-mono text-sm">
                    <h3 class="text-sky-400 font-bold mb-3">📁 Jekyll Directory Tree</h3>
<pre class="text-xs leading-5">my-jekyll-site/
├── _includes/
│   ├── header.html        # Sticky top navigation bar
│   └── sidebar.html       # Left category navigation menu
├── _layouts/
│   ├── default.html       # Base HTML wrapper (scripts, fonts)
│   └── doc.html           # Documentation layout with 3-column grid
├── assets/
│   └── css/
│       └── main.css       # Tailwind directives (@tailwind base;)
├── _config.yml            # Jekyll settings
├── tailwind.config.js     # Tailwind CSS configuration
└── index.md               # Main documentation content in Markdown</pre>
                </div>

                <!-- File 1: _layouts/default.html -->
                <div class="space-y-2">
                    <div class="flex items-center justify-between font-mono text-sm text-slate-700 dark:text-slate-300">
                        <span class="font-bold">1. _layouts/default.html</span>
                    </div>
                    <div class="relative rounded-xl overflow-hidden bg-slate-950 border border-slate-800">
                        <pre class="p-4 text-xs text-slate-200 overflow-x-auto"><code>&lt;!DOCTYPE html&gt;
&lt;html lang="en" class="scroll-smooth"&gt;
&lt;head&gt;
  &lt;meta charset="UTF-8"&gt;
  &lt;meta name="viewport" content="width=device-width, initial-scale=1.0"&gt;
  &lt;title&gt;{{ page.title }} | {{ site.title }}&lt;/title&gt;
  &lt;link rel="stylesheet" href="{{ '/assets/css/main.css' | relative_url }}"&gt;
  &lt;script src="https://cdn.tailwindcss.com"&gt;&lt;/script&gt;
&lt;/head&gt;
&lt;body class="bg-white text-slate-700 dark:bg-slate-900 dark:text-slate-300"&gt;
  {{ content }}
&lt;/body&gt;
&lt;/html&gt;</code></pre>
                    </div>
                </div>

                <!-- File 2: _layouts/doc.html -->
                <div class="space-y-2">
                    <div class="flex items-center justify-between font-mono text-sm text-slate-700 dark:text-slate-300">
                        <span class="font-bold">2. _layouts/doc.html</span>
                    </div>
                    <div class="relative rounded-xl overflow-hidden bg-slate-950 border border-slate-800">
                        <pre class="p-4 text-xs text-slate-200 overflow-x-auto"><code>---
layout: default
---
{% include header.html %}

&lt;div class="max-w-8xl mx-auto px-4 sm:px-6 lg:px-8"&gt;
  &lt;div class="flex min-h-screen"&gt;
    {% include sidebar.html %}
    
    &lt;main class="flex-1 min-w-0 py-8 lg:px-12"&gt;
      &lt;div class="border-b border-slate-200 dark:border-slate-800 pb-6 mb-8"&gt;
        &lt;h1 class="text-4xl font-extrabold text-slate-900 dark:text-white"&gt;{{ page.title }}&lt;/h1&gt;
        {% if page.description %}
          &lt;p class="text-lg text-slate-600 dark:text-slate-400 mt-2"&gt;{{ page.description }}&lt;/p&gt;
        {% endif %}
      &lt;/div&gt;

      {{ content }}
    &lt;/main&gt;
  &lt;/div&gt;
&lt;/div&gt;</code></pre>
                    </div>
                </div>

                <!-- File 3: index.md -->
                <div class="space-y-2">
                    <div class="flex items-center justify-between font-mono text-sm text-slate-700 dark:text-slate-300">
                        <span class="font-bold">3. index.md (Sample Markdown Doc)</span>
                    </div>
                    <div class="relative rounded-xl overflow-hidden bg-slate-950 border border-slate-800">
                        <pre class="p-4 text-xs text-slate-200 overflow-x-auto"><code>---
layout: doc
title: Welcome to Documentation
description: Getting started with our platform and framework.
---

## Overview
This is a standard markdown document automatically compiled into the layout.

```html
&lt;div class="p-4 bg-sky-500 text-white"&gt;Tailwind styled block&lt;/div&gt;
```</code></pre>
                    </div>
                </div>

            </div>
        </div>

    </div>

    <!-- Toast Notification for Copy Clipboard -->
    <div id="toast" class="fixed bottom-5 right-5 z-50 bg-slate-900 text-white dark:bg-sky-500 text-sm px-4 py-2.5 rounded-lg shadow-xl translate-y-20 opacity-0 transition-all duration-300 flex items-center gap-2">
        <i class="fa-solid fa-check text-emerald-400 dark:text-slate-900"></i>
        <span>Copied to clipboard!</span>
    </div>

    <!-- JavaScript Logic -->
    <script>
        // Theme toggling logic
        const themeToggleBtn = document.getElementById('theme-toggle');
        const darkIcon = document.getElementById('theme-toggle-dark-icon');
        const lightIcon = document.getElementById('theme-toggle-light-icon');

        if (localStorage.getItem('color-theme') === 'dark' || (!('color-theme' in localStorage) && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
            document.documentElement.classList.add('dark');
            lightIcon.classList.remove('hidden');
        } else {
            document.documentElement.classList.remove('dark');
            darkIcon.classList.remove('hidden');
        }

        themeToggleBtn.addEventListener('click', function() {
            darkIcon.classList.toggle('hidden');
            lightIcon.classList.toggle('hidden');

            if (document.documentElement.classList.contains('dark')) {
                document.documentElement.classList.remove('dark');
                localStorage.setItem('color-theme', 'light');
            } else {
                document.documentElement.classList.add('dark');
                localStorage.setItem('color-theme', 'dark');
            }
        });

        // View Switcher (Docs Preview vs Jekyll Code)
        function switchView(view) {
            const docsView = document.getElementById('docs-view');
            const jekyllView = document.getElementById('jekyll-view');
            const docsBtn = document.getElementById('tab-btn-docs');
            const jekyllBtn = document.getElementById('tab-btn-jekyll');

            if (view === 'docs') {
                docsView.classList.remove('hidden');
                jekyllView.classList.add('hidden');
                docsBtn.className = "px-3 py-1 rounded-md bg-white dark:bg-slate-700 text-sky-600 dark:text-sky-400 shadow-sm transition";
                jekyllBtn.className = "px-3 py-1 rounded-md text-slate-600 dark:text-slate-400 hover:text-slate-900 dark:hover:text-white transition";
            } else {
                docsView.classList.add('hidden');
                jekyllView.classList.remove('hidden');
                jekyllBtn.className = "px-3 py-1 rounded-md bg-white dark:bg-slate-700 text-sky-600 dark:text-sky-400 shadow-sm transition";
                docsBtn.className = "px-3 py-1 rounded-md text-slate-600 dark:text-slate-400 hover:text-slate-900 dark:hover:text-white transition";
            }
        }

        // Mobile drawer navigation toggle
        const mobileBtn = document.getElementById('mobile-menu-btn');
        const sidebar = document.getElementById('sidebar');
        const backdrop = document.getElementById('mobile-sidebar-backdrop');

        function toggleMobileMenu() {
            sidebar.classList.toggle('-translate-x-full');
            backdrop.classList.toggle('hidden');
        }

        mobileBtn.addEventListener('click', toggleMobileMenu);
        backdrop.addEventListener('click', toggleMobileMenu);

        // Copy Code Functionality
        function copyCode(button) {
            const container = button.closest('.group');
            const codeText = container.querySelector('code').innerText;

            // Fallback for copy command
            const tempTextArea = document.createElement('textarea');
            tempTextArea.value = codeText;
            document.body.appendChild(tempTextArea);
            tempTextArea.select();
            document.execCommand('copy');
            document.body.removeChild(tempTextArea);

            // Toast feedback
            const toast = document.getElementById('toast');
            toast.classList.remove('translate-y-20', 'opacity-0');
            setTimeout(() => {
                toast.classList.add('translate-y-20', 'opacity-0');
            }, 2000);
        }

        // Quick Search Shortcut Focus
        document.addEventListener('keydown', (e) => {
            if (e.key === '/' || (e.metaKey && e.key === 'k')) {
                const searchInput = document.getElementById('doc-search-input');
                if (document.activeElement !== searchInput) {
                    e.preventDefault();
                    searchInput.focus();
                }
            }
        });
    </script>
</body>
</html>