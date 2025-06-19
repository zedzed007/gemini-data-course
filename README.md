<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Course: Data Analysis with Google Gemini</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <!-- Chart.js Boxplot Controller - for boxplot support. Note: If this fails, Chart.js will fallback or need adjustment. -->
    <script src="https://cdn.jsdelivr.net/npm/@sgratzl/chartjs-chart-boxplot"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <style>
        body { font-family: 'Inter', sans-serif; background-color: #f8fafc; color: #334155; }
        .chart-container { position: relative; width: 100%; max-width: 600px; margin-left: auto; margin-right: auto; height: 350px; max-height: 400px; }
        @media (min-width: 768px) { .chart-container { height: 400px; } }
        .tab-button.active { background-color: #059669; color: white; }
        .tab-button { transition: all 0.3s ease; }
        .tab-content { display: none; }
        .tab-content.active { display: block; }
        .timeline-item::before { content: ''; position: absolute; top: 1rem; left: 1rem; transform: translateX(-50%); width: 2px; height: 100%; background-color: #cbd5e1; z-index: -1; }
        .timeline-item:last-child::before { display: none; }
        .timeline-dot { box-shadow: 0 0 0 4px white, inset 0 2px 0 rgba(0,0,0,0.08), 0 3px 0 4px rgba(0,0,0,0.05); }
        details > summary { list-style: none; cursor: pointer; padding: 1.25rem 1.5rem; background-color: #f0f9ff; border-radius: 0.75rem; font-weight: 600; display: flex; justify-content: space-between; align-items: center; transition: background-color 0.3s ease, transform 0.2s ease; box-shadow: 0 2px 5px rgba(0,0,0,0.05); }
        details > summary:hover { background-color: #e0f2fe; transform: translateY(-2px); }
        details[open] > summary { background-color: #dbeafe; box-shadow: 0 4px 10px rgba(0,0,0,0.1); }
        details > summary::-webkit-details-marker { display: none; }
        details > summary:after { content: '+'; font-size: 1.5rem; font-weight: bold; color: #3b82f6; transition: transform 0.2s ease; }
        details[open] > summary:after { content: '-'; transform: rotate(0deg); }
        details .module-content { padding: 1rem 1.5rem 1.5rem; background-color: #ffffff; border-radius: 0 0 0.75rem 0.75rem; box-shadow: 0 5px 15px rgba(0,0,0,0.08); margin-top: -0.5rem; border-top: 2px solid #a7d0ff; }
    </style>
</head>
<body class="antialiased">

    <header class="bg-white shadow-sm sticky top-0 z-50">
        <nav class="container mx-auto px-6 py-4 flex justify-between items-center">
            <div class="text-2xl font-bold text-emerald-700">Gemini Data Analysis Course</div>
            <div class="hidden md:flex items-center space-x-8">
                <a href="#overview" class="text-slate-600 hover:text-emerald-700 font-medium">Overview</a>
                <a href="#learning-hub" class="text-slate-600 hover:text-emerald-700 font-medium">Learning Hub</a>
                <a href="#journey" class="text-slate-600 hover:text-emerald-700 font-medium">Journey</a>
                <a href="#resources" class="text-slate-600 hover:text-emerald-700 font-medium">Resources</a>
            </div>
        </nav>
    </header>

    <main>
        <section id="hero" class="bg-slate-800 text-white py-20 md:py-32">
            <div class="container mx-auto px-6 text-center">
                <h1 class="text-4xl md:text-6xl font-extrabold tracking-tight mb-4">Master Data Analysis with Conversational AI</h1>
                <p class="text-lg md:text-xl text-slate-300 max-w-3xl mx-auto mb-8">Transform raw data into powerful insights using plain English. This interactive guide teaches you how to leverage Google Gemini for efficient and intuitive data analysis, focusing on core skills and effective prompting.</p>
                <a href="#learning-hub" class="bg-emerald-500 hover:bg-emerald-600 text-white font-bold py-3 px-8 rounded-full text-lg transition duration-300 transform hover:scale-105">Start Learning Now</a>
            </div>
        </section>

        <section id="overview" class="py-16 md:py-24">
            <div class="container mx-auto px-6 text-center">
                <h2 class="text-3xl md:text-4xl font-bold text-slate-800 mb-4">Why Learn Data Analysis with Gemini?</h2>
                <p class="text-lg text-slate-600 max-w-2xl mx-auto mb-12">This course focuses on a revolutionary approach. Instead of memorizing complex code, you'll master the art of asking the right questions. Gemini acts as your personal data assistant, accelerating your workflow from hours to minutes and making data analysis truly intuitive.</p>
                <div class="grid md:grid-cols-3 gap-8">
                    <div class="bg-white p-8 rounded-xl shadow-lg hover:shadow-emerald-100 hover:-translate-y-2 transition-all duration-300">
                        <div class="text-4xl mb-4">⚡️</div>
                        <h3 class="text-xl font-semibold text-slate-900 mb-2">Accelerated Insight Discovery</h3>
                        <p class="text-slate-500">Get from raw data to actionable insights faster than ever by removing the barrier of complex syntax, focusing purely on results.</p>
                    </div>
                    <div class="bg-white p-8 rounded-xl shadow-lg hover:shadow-emerald-100 hover:-translate-y-2 transition-all duration-300">
                        <div class="text-4xl mb-4">🧠</div>
                        <h3 class="text-xl font-semibold text-slate-900 mb-2">Intuitive Analytical Thinking</h3>
                        <p class="text-slate-500">Focus on the 'why' and 'what' of data analysis. Understand core concepts without getting bogged down in implementation details.</p>
                    </div>
                    <div class="bg-white p-8 rounded-xl shadow-lg hover:shadow-emerald-100 hover:-translate-y-2 transition-all duration-300">
                        <div class="text-4xl mb-4">💬</div>
                        <h3 class="text-xl font-semibold text-slate-900 mb-2">Powerful Iterative Exploration</h3>
                        <p class="text-slate-500">Effortlessly ask follow-up questions, refine your analysis, and dig deeper into your data with simple, dynamic conversation.</p>
                    </div>
                </div>
            </div>
        </section>

        <section id="learning-hub" class="py-16 md:py-24 bg-slate-50">
            <div class="container mx-auto px-6">
                <div class="text-center">
                    <h2 class="text-3xl md:text-4xl font-bold text-slate-800 mb-4">Interactive Learning Hub</h2>
                    <p class="text-lg text-slate-600 max-w-2xl mx-auto mb-12">This is where the hands-on learning happens. Select a data analysis skill to explore how to perform key tasks with conversational prompts. The "Analyze & Visualize" tab is fully interactive, demonstrating Gemini's power!</p>
                </div>

                <div class="bg-white rounded-xl shadow-2xl p-4 md:p-8">
                    <div class="flex flex-wrap justify-center border-b border-slate-200 mb-8">
                        <button class="tab-button text-lg font-medium py-3 px-6 text-slate-500 border-b-4 border-transparent hover:bg-slate-100 active" data-tab="inspect">1. Inspect Data</button>
                        <button class="tab-button text-lg font-medium py-3 px-6 text-slate-500 border-b-4 border-transparent hover:bg-slate-100" data-tab="clean">2. Clean & Manipulate</button>
                        <button class="tab-button text-lg font-medium py-3 px-6 text-slate-500 border-b-4 border-transparent hover:bg-slate-100" data-tab="analyze">3. Analyze & Visualize</button>
                        <button class="tab-button text-lg font-medium py-3 px-6 text-slate-500 border-b-4 border-transparent hover:bg-slate-100" data-tab="prompting">4. Master Prompting</button>
                    </div>

                    <div id="inspect" class="tab-content active">
                        <h3 class="text-2xl font-semibold text-slate-700 mb-4">Skill: Initial Data Inspection</h3>
                        <p class="text-slate-600 mb-6">Before any analysis, you must understand your data's structure and quality. Use these prompts to get a quick and comprehensive overview, just by asking Gemini.</p>
                        <div class="grid md:grid-cols-2 gap-6">
                            <div>
                                <p class="font-semibold mb-2">Your Prompt:</p>
                                <code class="block bg-slate-100 text-slate-800 p-3 rounded-md mb-4 text-sm font-mono">"Show me the first 5 rows of the data."</code>
                                <p class="font-semibold mb-2">Gemini's Output (Example):</p>
                                <div class="overflow-x-auto bg-slate-100 p-3 rounded-md">
                                    <table class="w-full text-left text-sm">
                                        <thead class="bg-slate-200"><tr><th class="p-2">Country</th><th class="p-2">Age</th><th class="p-2">Score</th></tr></thead>
                                        <tbody>
                                            <tr class="border-t border-slate-200"><td>USA</td><td>25</td><td>8.5</td></tr>
                                            <tr class="border-t border-slate-200"><td>Canada</td><td>34</td><td>7.2</td></tr>
                                            <tr class="border-t border-slate-200"><td>USA</td><td>29</td><td>9.1</td></tr>
                                        </tbody>
                                    </table>
                                </div>
                            </div>
                             <div>
                                <p class="font-semibold mb-2">Your Prompt:</p>
                                <code class="block bg-slate-100 text-slate-800 p-3 rounded-md mb-4 text-sm font-mono">"Provide descriptive statistics for numerical columns."</code>
                                <p class="font-semibold mb-2">Gemini's Output (Example):</p>
                                <div class="overflow-x-auto bg-slate-100 p-3 rounded-md">
                                     <table class="w-full text-left text-sm">
                                        <thead class="bg-slate-200"><tr><th class="p-2">Statistic</th><th class="p-2">Age</th><th class="p-2">Score</th></tr></thead>
                                        <tbody>
                                            <tr class="border-t border-slate-200"><td>count</td><td>150.0</td><td>150.0</td></tr>
                                            <tr class="border-t border-slate-200"><td>mean</td><td>28.5</td><td>7.8</td></tr>
                                            <tr class="border-t border-slate-200"><td>std</td><td>5.2</td><td>1.3</td></tr>
                                            <tr class="border-t border-slate-200"><td>min</td><td>18.0</td><td>4.1</td></tr>
                                            <tr class="border-t border-slate-200"><td>max</td><td>45.0</td><td>9.9</td></tr>
                                        </tbody>
                                    </table>
                                </div>
                            </div>
                        </div>
                    </div>

                    <div id="clean" class="tab-content">
                        <h3 class="text-2xl font-semibold text-slate-700 mb-4">Skill: Data Cleaning and Manipulation</h3>
                        <p class="text-slate-600 mb-6">Raw data is rarely perfect. Use simple prompts to handle missing values, remove duplicates, or even create new, more useful columns for your analysis, all conversationally.</p>
                        <div class="space-y-4">
                            <details class="bg-white rounded-lg shadow-sm">
                                <summary class="font-medium text-slate-800 p-4 cursor-pointer flex justify-between items-center">Handling Missing Values <span class="text-2xl text-emerald-500 font-light">+</span></summary>
                                <div class="p-4 border-t border-slate-200">
                                    <p class="font-semibold mb-2">Prompt Example:</p>
                                    <code class="block bg-slate-100 p-3 rounded-md my-2 text-sm font-mono">"Fill any missing values in the 'Income' column with the median income."</code>
                                    <p class="text-slate-600 text-sm">**Insight:** This is a robust way to handle missing numerical data, as the median is not affected by extreme outliers. Gemini understands common imputation strategies directly from your prompt.</p>
                                </div>
                            </details>
                             <details class="bg-white rounded-lg shadow-sm">
                                <summary class="font-medium text-slate-800 p-4 cursor-pointer flex justify-between items-center">Removing Duplicates <span class="text-2xl text-emerald-500 font-light">+</span></summary>
                                <div class="p-4 border-t border-slate-200">
                                    <p class="font-semibold mb-2">Prompt Example:</p>
                                    <code class="block bg-slate-100 p-3 rounded-md my-2 text-sm font-mono">"Remove any duplicate rows based on 'CustomerID', keeping the first one."</code>
                                    <p class="text-slate-600 text-sm">**Insight:** This ensures each customer or record is represented only once, preventing inflated counts and skewed statistics, crucial for accurate analysis.</p>
                                </div>
                            </details>
                             <details class="bg-white rounded-lg shadow-sm">
                                <summary class="font-medium text-slate-800 p-4 cursor-pointer flex justify-between items-center">Creating New Columns (Feature Engineering) <span class="text-2xl text-emerald-500 font-light">+</span></summary>
                                <div class="p-4 border-t border-slate-200">
                                    <p class="font-semibold mb-2">Prompt Example:</p>
                                    <code class="block bg-slate-100 p-3 rounded-md my-2 text-sm font-mono">"Create a new column 'AgeGroup'. If Age is under 30, it's 'Young Adult', otherwise it's 'Adult'."</code>
                                    <p class="text-slate-600 text-sm">**Insight:** This transforms a numerical column into a categorical one, which is perfect for comparative analysis. You can categorize data based on any logical conditions.</p>
                                </div>
                            </details>
                             <details class="bg-white rounded-lg shadow-sm">
                                <summary class="font-medium text-slate-800 p-4 cursor-pointer flex justify-between items-center">Correcting Data Types <span class="text-2xl text-emerald-500 font-light">+</span></summary>
                                <div class="p-4 border-t border-slate-200">
                                    <p class="font-semibold mb-2">Prompt Example:</p>
                                    <code class="block bg-slate-100 p-3 rounded-md my-2 text-sm font-mono">"Convert the 'Order_Date' column to a datetime format."</code>
                                    <p class="text-slate-600 text-sm">**Insight:** Ensuring correct data types is fundamental. If dates are text, you can't sort chronologically or extract months. Gemini handles the conversion effortlessly.</p>
                                </div>
                            </details>
                        </div>
                    </div>

                    <div id="analyze" class="tab-content">
                         <h3 class="text-2xl font-semibold text-slate-700 mb-4">Skill: Analyze & Visualize Insights</h3>
                         <p class="text-slate-600 mb-6">This is where data becomes a story. Select an analysis task below to see the prompt you would use and the resulting visualization generated directly by Gemini. Click different buttons to see the chart update!</p>
                        <div class="flex flex-wrap justify-center gap-3 mb-8">
                            <button class="viz-button bg-emerald-500 text-white py-2 px-4 rounded-full text-sm font-medium" data-viz="bar">Compare Averages</button>
                            <button class="viz-button bg-slate-200 text-slate-700 py-2 px-4 rounded-full text-sm font-medium" data-viz="scatter">Find Correlation</button>
                            <button class="viz-button bg-slate-200 text-slate-700 py-2 px-4 rounded-full text-sm font-medium" data-viz="box">Compare Distributions</button>
                        </div>
                        <div class="grid md:grid-cols-2 gap-8 items-center">
                            <div class="bg-slate-100 p-4 rounded-lg">
                                 <p class="font-semibold mb-2">Your Prompt:</p>
                                 <code id="viz-prompt" class="block bg-white text-emerald-800 p-3 rounded-md mb-4 text-sm font-mono">"Create a professional bar chart showing the average Addicted_Score for each Most_Used_Platform."</code>
                                 <p class="font-semibold mb-2">The Insight:</p>
                                 <p id="viz-insight" class="text-slate-600 text-sm">This chart quickly reveals which social media platforms are associated with higher average addiction scores, providing a clear target for further investigation or intervention strategies.</p>
                            </div>
                            <div class="chart-container">
                                <canvas id="analysisChart"></canvas>
                            </div>
                        </div>
                    </div>

                    <div id="prompting" class="tab-content">
                        <h3 class="text-2xl font-semibold text-slate-700 mb-4">Skill: Mastering Effective Prompting</h3>
                        <p class="text-slate-600 mb-6">Your success with Gemini depends on how well you communicate your analytical goals. Here are core principles and advanced strategies to guide you in crafting powerful prompts.</p>
                        <div class="grid md:grid-cols-2 gap-6">
                            <div class="bg-emerald-50 p-6 rounded-lg">
                                <h4 class="font-bold text-emerald-800 text-lg mb-2">Be Clear and Specific</h4>
                                <p class="text-slate-600">Avoid ambiguity. Use exact column names. Instead of "show big users," say "Filter for students with 'Avg_Daily_Usage_Hours' greater than 6." Specify output format: "Give me a Markdown table."</p>
                            </div>
                             <div class="bg-emerald-50 p-6 rounded-lg">
                                <h4 class="font-bold text-emerald-800 text-lg mb-2">Break Down Complex Tasks</h4>
                                <p class="text-slate-600">If a request has multiple steps, ask them one by one. Filter first, then calculate an average, then create a plot. This ensures accuracy and allows for iterative refinement.</p>
                            </div>
                             <div class="bg-emerald-50 p-6 rounded-lg">
                                <h4 class="font-bold text-emerald-800 text-lg mb-2">Iterate and Refine Your Questions</h4>
                                <p class="text-slate-600">Data analysis is a conversation. If a chart isn't quite right, ask for a change. "That's good, but can you change the bar colors to blue?" or "Add a title to the previous chart."</p>
                            </div>
                             <div class="bg-emerald-50 p-6 rounded-lg">
                                <h4 class="font-bold text-emerald-800 text-lg mb-2">Ask "Why?" to Dig Deeper</h4>
                                <p class="text-slate-600">If you see a surprising result, ask Gemini to help you investigate the underlying reasons. "Sales dropped in March. Can you show me the sales for each product category in March?"</p>
                            </div>
                             <div class="bg-emerald-50 p-6 rounded-lg">
                                <h4 class="font-bold text-emerald-800 text-lg mb-2">Leverage Contextual Memory</h4>
                                <p class="text-slate-600">Gemini remembers previous interactions. You can refer to "the data I just filtered" or "the previous table" without re-stating all details.</p>
                            </div>
                             <div class="bg-emerald-50 p-6 rounded-lg">
                                <h4 class="font-bold text-emerald-800 text-lg mb-2">Explore Feature Engineering</h4>
                                <p class="text-slate-600">Don't limit yourself to existing columns. Ask Gemini to create new, insightful features like "Add a 'Profit_Margin' column as ('Revenue' - 'Cost') / 'Revenue'."</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section id="journey" class="py-16 md:py-24">
             <div class="container mx-auto px-6">
                <div class="text-center">
                    <h2 class="text-3xl md:text-4xl font-bold text-slate-800 mb-4">Your Data Analysis Journey</h2>
                    <p class="text-lg text-slate-600 max-w-2xl mx-auto mb-16">The course is structured to build your skills logically, from fundamental concepts to advanced analytical thinking, all within the Gemini conversational environment.</p>
                </div>
                <div class="relative">
                    <div class="timeline-item relative pl-8 pb-8">
                        <div class="absolute top-4 left-0 w-8 text-center"><div class="mx-auto w-4 h-4 rounded-full bg-emerald-500 timeline-dot"></div></div>
                        <h4 class="font-bold text-emerald-700 text-xl mb-1">Module 1: Getting Started with Gemini</h4>
                        <p class="text-slate-600">Master the basics of interacting with Gemini for data analysis, including efficient data uploading and crucial initial data inspection techniques.</p>
                    </div>
                    <div class="timeline-item relative pl-8 pb-8">
                         <div class="absolute top-4 left-0 w-8 text-center"><div class="mx-auto w-4 h-4 rounded-full bg-emerald-500 timeline-dot"></div></div>
                        <h4 class="font-bold text-emerald-700 text-xl mb-1">Modules 2 & 4: Data Transformation & Cleaning Mastery</h4>
                        <p class="text-slate-600">Acquire essential skills in cleaning real-world data: handling missing values, removing duplicates, correcting data types, and creating powerful new features conversationally.</p>
                    </div>
                     <div class="timeline-item relative pl-8 pb-8">
                         <div class="absolute top-4 left-0 w-8 text-center"><div class="mx-auto w-4 h-4 rounded-full bg-emerald-500 timeline-dot"></div></div>
                        <h4 class="font-bold text-emerald-700 text-xl mb-1">Module 3: Uncovering Insights & Trends</h4>
                        <p class="text-slate-600">Dive into core analytical techniques. Learn to summarize, compare groups, identify correlations, and use compelling visualizations to tell a powerful story with your data.</p>
                    </div>
                    <div class="timeline-item relative pl-8">
                        <div class="absolute top-4 left-0 w-8 text-center"><div class="mx-auto w-4 h-4 rounded-full bg-emerald-500 timeline-dot"></div></div>
                        <h4 class="font-bold text-emerald-700 text-xl mb-1">Module 5: Advanced Prompting & Analytical Proficiency</h4>
                        <p class="text-slate-600">Go beyond basic prompts. Develop advanced prompting strategies, learn effective data storytelling techniques, and cultivate the critical thinking mindset of a seasoned data analyst.</p>
                    </div>
                </div>
            </div>
        </section>

        <section id="resources" class="py-16 md:py-24 bg-slate-800 text-white">
            <div class="container mx-auto px-6 text-center">
                <h2 class="text-3xl md:text-4xl font-bold mb-4">Continuous Growth & Resources</h2>
                <p class="text-lg text-slate-300 max-w-2xl mx-auto mb-12">This course is your launchpad. To truly master data analysis, complement your new Gemini skills by deepening your understanding of these fundamental concepts and through continuous practice.</p>
                <div class="grid md:grid-cols-3 gap-8">
                    <div class="bg-slate-700 p-8 rounded-xl shadow-lg">
                        <h3 class="text-xl font-semibold text-emerald-400 mb-2">Statistical Fundamentals</h3>
                        <p class="text-slate-300">A strong grasp of descriptive and inferential statistics is crucial to asking the right questions and accurately interpreting Gemini's analytical outputs.</p>
                    </div>
                    <div class="bg-slate-700 p-8 rounded-xl shadow-lg">
                        <h3 class="text-xl font-semibold text-emerald-400 mb-2">Data Visualization Principles</h3>
                        <p class="text-slate-300">Learn the art and science behind creating clear, impactful, and unbiased data visualizations that effectively convey your insights and tell a compelling story.</p>
                    </div>
                    <div class="bg-slate-700 p-8 rounded-xl shadow-lg">
                        <h3 class="text-xl font-semibold text-emerald-400 mb-2">Practice with Diverse Datasets</h3>
                        <p class="text-slate-300">Regularly apply your conversational data analysis skills to new and varied datasets from different domains to solidify your learning and build intuition.</p>
                    </div>
                </div>
            </div>
        </section>
    </main>

    <footer class="bg-slate-900 py-8">
        <div class="container mx-auto px-6 text-center text-slate-400">
            <p>&copy; 2025 Interactive Gemini Data Analysis Course. All rights reserved.</p>
            <p class="mt-2">Designed with passion for data and conversational intelligence.</p>
        </div>
    </footer>

    <script>
        document.addEventListener('DOMContentLoaded', function () {
            const tabs = document.querySelectorAll('.tab-button');
            const tabContents = document.querySelectorAll('.tab-content');

            tabs.forEach(tab => {
                tab.addEventListener('click', () => {
                    tabs.forEach(item => {
                        item.classList.remove('active', 'bg-emerald-500', 'text-white');
                        item.classList.add('bg-slate-200', 'text-slate-700');
                    });
                    tab.classList.add('active', 'bg-emerald-500', 'text-white');
                    tab.classList.remove('bg-slate-200', 'text-slate-700');

                    const target = document.getElementById(tab.dataset.tab);
                    tabContents.forEach(content => content.classList.remove('active'));
                    target.classList.add('active');
                });
            });
            
            const vizButtons = document.querySelectorAll('.viz-button');
            const promptEl = document.getElementById('viz-prompt');
            const insightEl = document.getElementById('viz-insight');
            const ctx = document.getElementById('analysisChart').getContext('2d');
            let analysisChart;

            const baseLabels = ['Most_Used_Platform A', 'Most_Used_Platform B', 'Most_Used_Platform C', 'Most_Used_Platform D'];
            const generateRandomData = (count, min, max) => Array.from({length: count}, () => parseFloat((Math.random() * (max - min) + min).toFixed(1)));
            const generateBoxPlotData = (n) => {
                const data = [];
                for (let i = 0; i < n; i++) {
                    const values = Array.from({length: 20}, () => parseFloat((Math.random() * (10 - 3) + 3).toFixed(1))).sort((a,b)=>a-b);
                    data.push(values);
                }
                return data;
            };

            const chartData = {
                bar: {
                    type: 'bar',
                    data: {
                        labels: baseLabels,
                        datasets: [{
                            label: 'Avg Addiction Score',
                            data: generateRandomData(4, 6, 9),
                            backgroundColor: ['#10b981', '#06b6d4', '#3b82f6', '#6366f1'],
                            borderColor: '#ffffff',
                            borderWidth: 2
                        }]
                    },
                    options: { responsive: true, maintainAspectRatio: false, plugins: { legend: { display: false } }, scales: { y: { beginAtZero: true, grid: { color: '#e2e8f0' }, title: { display: true, text: 'Average Addiction Score' } }, x: { grid: { display: false }, title: { display: true, text: 'Most Used Platform' }, ticks: { callback: function(value, index, values) { return this.getLabelForValue(value).length > 16 ? this.getLabelForValue(value).substring(0, 15) + '...' : this.getLabelForValue(value); } } } } }
                },
                scatter: {
                    type: 'scatter',
                    data: {
                        datasets: [{
                            label: 'Usage vs Score',
                            data: Array.from({length: 20}, () => ({x: parseFloat((Math.random() * 8 + 1).toFixed(1)), y: parseFloat((Math.random() * 5 + 5).toFixed(1))})).sort((a, b) => a.x - b.x),
                            backgroundColor: '#059669',
                            pointRadius: 6,
                            pointHoverRadius: 8,
                            tooltip: { callbacks: { label: function(context) { return `Usage: ${context.parsed.x}h, Score: ${context.parsed.y}`; } } }
                        }]
                    },
                    options: { responsive: true, maintainAspectRatio: false, plugins: { legend: { display: false } }, scales: { x: { type: 'linear', position: 'bottom', title: { display: true, text: 'Avg Daily Usage (Hours)' }, grid: { display: false } }, y: { title: { display: true, text: 'Addiction Score' }, grid: { color: '#e2e8f0' } } } }
                },
                box: {
                    type: 'boxplot',
                    data: {
                        labels: ['Undergraduate', 'Graduate', 'Doctorate'],
                        datasets: [{
                            label: 'Usage Hours Distribution',
                            data: generateBoxPlotData(3),
                             backgroundColor: '#a7f3d0',
                             borderColor: '#047857',
                             borderWidth: 2,
                             outlierColor: '#f97316',
                             padding: 10
                        }]
                    },
                    options: { responsive: true, maintainAspectRatio: false, plugins: { legend: { display: false } }, scales: { y: { title: { display: true, text: 'Avg Daily Usage (Hours)'}, grid: { color: '#e2e8f0' }, ticks: { callback: function(value) { return value.toFixed(1); } } } } }
                }
            };

            const vizInfo = {
                bar: {
                    prompt: `"Create a professional bar chart showing the average Addicted_Score for each Most_Used_Platform."`,
                    insight: `This chart quickly reveals which social media platforms are associated with higher average addiction scores among users. Visualizing averages across categories helps in identifying key areas that might require closer examination or targeted strategies.`
                },
                scatter: {
                    prompt: `"Generate a scatter plot to visualize the relationship between Avg_Daily_Usage_Hours and Addicted_Score, and suggest a trend."`,
                    insight: `This plot visually helps to identify patterns between two numerical variables. A clear upward trend here suggests that as daily usage hours increase, the addiction score also tends to increase, indicating a strong positive relationship.`
                },
                box: {
                    prompt: `"Create a box plot to compare the distribution of Avg_Daily_Usage_Hours across different Academic_Levels."`,
                    insight: `Box plots are excellent for comparing the spread and central tendency of a numerical variable across different categories. Here, we can easily see the median usage, the interquartile range (middle 50% of data), and identify any outliers in daily usage hours for each academic group. This allows for quick comparative analysis of distributions.`
                }
            };
            
            function renderChart(vizType) {
                if (analysisChart) {
                    analysisChart.destroy();
                }
                
                const config = chartData[vizType];
                analysisChart = new Chart(ctx, config);
                promptEl.textContent = vizInfo[vizType].prompt;
                insightEl.textContent = vizInfo[vizType].insight;
            }

            vizButtons.forEach(button => {
                button.addEventListener('click', () => {
                    vizButtons.forEach(btn => {
                        btn.classList.remove('bg-emerald-500', 'text-white');
                        btn.classList.add('bg-slate-200', 'text-slate-700');
                    });
                    button.classList.add('bg-emerald-500', 'text-white');
                    button.classList.remove('bg-slate-200', 'text-slate-700');
                    renderChart(button.dataset.viz);
                });
            });

            // Initial render of the default chart
            renderChart('bar');

            // Set initial active tab button style
            document.querySelector('.tab-button.active').classList.add('bg-emerald-500', 'text-white');
            document.querySelector('.tab-button.active').classList.remove('bg-slate-200', 'text-slate-700');
        });
    </script>
</body>
</html>
