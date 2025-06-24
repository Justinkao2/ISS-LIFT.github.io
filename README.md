<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive R Functions Handbook</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <!-- Chosen Palette: Warm Neutrals -->
    <!-- Application Structure Plan: A two-pane layout is used. The left pane is a collapsible navigation sidebar listing functions grouped by their source file. The right pane displays the details of the selected function. This structure is standard for documentation and highly intuitive, allowing users to easily browse the function list while reading detailed content without context switching. On mobile, the layout stacks vertically for usability. -->
    <!-- Visualization & Content Choices: Report Info: R function descriptions (purpose, arguments, returns). -> Goal: Provide a quick and easy reference guide. -> Viz/Presentation Method: Structured and styled text blocks within a dedicated content pane for each function. -> Interaction: User clicks a function name in the navigation sidebar, and JavaScript shows the corresponding details in the content pane. -> Justification: This is the most direct and efficient way to present reference documentation, prioritizing readability and speed. -> Library/Method: Vanilla JavaScript for click handling and content visibility toggling. Tailwind CSS for styling and layout. -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <style>
        body {
            font-family: 'Inter', sans-serif;
        }
        .content-section {
            display: none;
        }
        .content-section.active {
            display: block;
        }
        .nav-link.active {
            background-color: #e0f2fe; /* light blue */
            color: #0c4a6e; /* dark blue */
            font-weight: 600;
        }
        .nav-category-header {
            cursor: pointer;
        }
        .nav-category-header .arrow {
            transition: transform 0.2s ease-in-out;
        }
        .nav-category.collapsed .arrow {
            transform: rotate(-90deg);
        }
         .nav-category.collapsed .function-list {
            display: none;
        }
    </style>
</head>
<body class="bg-stone-50 text-stone-800">

    <div class="flex flex-col md:flex-row min-h-screen">
        <!-- Sidebar Navigation -->
        <nav id="sidebar" class="w-full md:w-72 lg:w-80 bg-white p-4 md:p-6 shadow-lg flex-shrink-0">
            <h1 class="text-2xl font-bold text-stone-900 mb-6">R Functions Handbook</h1>
            
            <div class="space-y-4">
                <!-- Modeling.r Section -->
                <div class="nav-category" id="nav-modeling">
                    <h2 class="nav-category-header text-lg font-semibold text-sky-800 flex justify-between items-center mb-2">
                        <span>modeling.r</span>
                        <span class="arrow text-sky-600">&#9660;</span>
                    </h2>
                    <ul class="function-list space-y-1 border-l-2 border-stone-200 pl-4">
                        <li><a href="#" class="nav-link block p-2 rounded-md hover:bg-stone-100" data-target="get_train_control">get_train_control</a></li>
                        <li><a href="#" class="nav-link block p-2 rounded-md hover:bg-stone-100" data-target="train_lift_model">train_lift_model</a></li>
                        <li><a href="#" class="nav-link block p-2 rounded-md hover:bg-stone-100" data-target="train_lift_model_withoutgrid">train_lift_model_withoutgrid</a></li>
                        <li><a href="#" class="nav-link block p-2 rounded-md hover:bg-stone-100" data-target="train_regular_model_withoutgrid">train_regular_model_withoutgrid</a></li>
                        <li><a href="#" class="nav-link block p-2 rounded-md hover:bg-stone-100" data-target="train_regular_model">train_regular_model</a></li>
                        <li><a href="#" class="nav-link block p-2 rounded-md hover:bg-stone-100" data-target="train_lift_model_with_weights">train_lift_model_with_weights</a></li>
                        <li><a href="#" class="nav-link block p-2 rounded-md hover:bg-stone-100" data-target="train_lift_model_withoutgrid_with_weights">train_lift_model_withoutgrid_with_weights</a></li>
                        <li><a href="#" class="nav-link block p-2 rounded-md hover:bg-stone-100" data-target="train_regular_model_with_weights">train_regular_model_with_weights</a></li>
                        <li><a href="#" class="nav-link block p-2 rounded-md hover:bg-stone-100" data-target="train_regular_model_withoutgrid_with_weights">train_regular_model_withoutgrid_with_weights</a></li>
                        <li><a href="#" class="nav-link block p-2 rounded-md hover:bg-stone-100" data-target="calculate_lift">calculate_lift</a></li>
                        <li><a href="#" class="nav-link block p-2 rounded-md hover:bg-stone-100" data-target="plot_decision_tree">plot_decision_tree</a></li>
                        <li><a href="#" class="nav-link block p-2 rounded-md hover:bg-stone-100" data-target="generate_charts">generate_charts</a></li>
                        <li><a href="#" class="nav-link block p-2 rounded-md hover:bg-stone-100" data-target="calculate_top_10_percent_lifts">calculate_top_10_percent_lifts</a></li>
                        <li><a href="#" class="nav-link block p-2 rounded-md hover:bg-stone-100" data-target="calculate_top_percent_lifts">calculate_top_percent_lifts</a></li>
                    </ul>
                </div>

                <!-- Data.r Section -->
                <div class="nav-category" id="nav-data">
                    <h2 class="nav-category-header text-lg font-semibold text-sky-800 flex justify-between items-center mb-2">
                        <span>data.r</span>
                        <span class="arrow text-sky-600">&#9660;</span>
                    </h2>
                    <ul class="function-list space-y-1 border-l-2 border-stone-200 pl-4">
                        <li><a href="#" class="nav-link block p-2 rounded-md hover:bg-stone-100" data-target="prepare_kaggle_Churn_telo">prepare_kaggle_Churn_telo</a></li>
                        <li><a href="#" class="nav-link block p-2 rounded-md hover:bg-stone-100" data-target="prepare_kaggle_Churn_telo_with_stratified">prepare_kaggle_Churn_telo_with_stratified</a></li>
                        <li><a href="#" class="nav-link block p-2 rounded-md hover:bg-stone-100" data-target="prepare_bank_dataset">prepare_bank_dataset</a></li>
                        <li><a href="#" class="nav-link block p-2 rounded-md hover:bg-stone-100" data-target="prepare_bank_dataset_with_stratified">prepare_bank_dataset_with_stratified</a></li>
                        <li><a href="#" class="nav-link block p-2 rounded-md hover:bg-stone-100" data-target="prepare_credit_data">prepare_credit_data</a></li>
                    </ul>
                </div>
            </div>
        </nav>

        <!-- Main Content -->
        <main id="main-content" class="flex-grow p-6 md:p-10 bg-stone-50">
            <div id="welcome" class="content-section active">
                <div class="text-center mt-16">
                    <h2 class="text-4xl font-bold text-stone-700">Welcome to the R Functions Handbook</h2>
                    <p class="mt-4 text-lg text-stone-600">This interactive application provides detailed documentation for a collection of R functions designed for data preparation and machine learning modeling. The functions are organized by their source files, `data.r` and `modeling.r`.</p>
                    <p class="mt-2 text-stone-500">Select a function from the navigation menu on the left to view its purpose, arguments, and return values. You can also collapse or expand the file sections by clicking on their titles.</p>
                </div>
            </div>

            <!-- Function Details -->
            <div id="get_train_control" class="content-section">
                <h2 class="text-3xl font-bold mb-4 text-stone-900">get_train_control(p)</h2>
                <div class="space-y-6 text-base text-stone-700 leading-relaxed">
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Purpose</h3>
                        <p>This function creates a `trainControl` object, which defines the settings for model training within the `caret` package. It's specifically configured for cross-validation and uses a custom `summaryFunction` to calculate LIFT as the primary metric for model selection.</p>
                    </div>
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Arguments</h3>
                        <p><code class="bg-stone-200 text-stone-800 rounded px-2 py-1">p</code>: A numeric value (between 0 and 1) representing the percentage of the data to consider for the LIFT calculation. For example, `p = 0.1` means LIFT at the top 10% of the predictions.</p>
                    </div>
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Returns</h3>
                        <p>A `trainControl` object.</p>
                    </div>
                </div>
            </div>

            <div id="train_lift_model" class="content-section">
                <h2 class="text-3xl font-bold mb-4 text-stone-900">train_lift_model(...)</h2>
                <div class="space-y-6 text-base text-stone-700 leading-relaxed">
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Purpose</h3>
                        <p>This function trains a machine learning model using the `caret` package, specifically optimizing for LIFT at a given `p` percentage. It allows for hyperparameter tuning using a `tune_grid`. If `tune_grid` is `NULL`, it delegates to `train_lift_model_withoutgrid`.</p>
                    </div>
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Arguments</h3>
                        <ul class="list-disc pl-5 space-y-2">
                            <li><code class="bg-stone-200 text-stone-800 rounded px-2 py-1">train_data</code>: The dataset to be used for training the model.</li>
                            <li><code class="bg-stone-200 text-stone-800 rounded px-2 py-1">test_data</code>: The dataset to be used for making predictions after the model is trained.</li>
                            <li><code class="bg-stone-200 text-stone-800 rounded px-2 py-1">target</code>: A string specifying the name of the target variable.</li>
                            <li><code class="bg-stone-200 text-stone-800 rounded px-2 py-1">method</code>: A string indicating the machine learning algorithm to use.</li>
                            <li><code class="bg-stone-200 text-stone-800 rounded px-2 py-1">tune_grid</code> (Optional): A data frame specifying the hyperparameter grid for tuning.</li>
                            <li><code class="bg-stone-200 text-stone-800 rounded px-2 py-1">p</code> (Optional): The percentage of data for LIFT calculation. Defaults to 0.1.</li>
                        </ul>
                    </div>
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Returns</h3>
                        <p>A list containing the trained `model`, `predictions`, and `runtime_sec`.</p>
                    </div>
                </div>
            </div>
            
            <div id="train_lift_model_withoutgrid" class="content-section">
                <h2 class="text-3xl font-bold mb-4 text-stone-900">train_lift_model_withoutgrid(...)</h2>
                <div class="space-y-6 text-base text-stone-700 leading-relaxed">
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Purpose</h3>
                        <p>Similar to `train_lift_model`, but this function trains a machine learning model without explicit hyperparameter tuning (`tuneGrid`). It still optimizes for LIFT.</p>
                    </div>
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Arguments</h3>
                        <ul class="list-disc pl-5 space-y-2">
                             <li><code class="bg-stone-200 text-stone-800 rounded px-2 py-1">train_data</code>: The training dataset.</li>
                             <li><code class="bg-stone-200 text-stone-800 rounded px-2 py-1">test_data</code>: The testing dataset.</li>
                             <li><code class="bg-stone-200 text-stone-800 rounded px-2 py-1">target</code>: The name of the target variable.</li>
                             <li><code class="bg-stone-200 text-stone-800 rounded px-2 py-1">method</code>: The machine learning algorithm to use.</li>
                             <li><code class="bg-stone-200 text-stone-800 rounded px-2 py-1">p</code> (Optional): The percentage of data for LIFT calculation. Defaults to 0.1.</li>
                        </ul>
                    </div>
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Returns</h3>
                        <p>A list containing the trained `model`, `predictions`, and `runtime_sec`.</p>
                    </div>
                </div>
            </div>

            <div id="train_regular_model_withoutgrid" class="content-section">
                <h2 class="text-3xl font-bold mb-4 text-stone-900">train_regular_model_withoutgrid(...)</h2>
                <div class="space-y-6 text-base text-stone-700 leading-relaxed">
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Purpose</h3>
                        <p>This function trains a machine learning model using the `caret` package, optimizing for "Accuracy" as the primary metric, and *without* using an explicit hyperparameter tuning grid.</p>
                    </div>
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Arguments</h3>
                        <ul class="list-disc pl-5 space-y-2">
                            <li><code class="bg-stone-200 text-stone-800 rounded px-2 py-1">train_data</code>, <code class="bg-stone-200 text-stone-800 rounded px-2 py-1">test_data</code>, <code class="bg-stone-200 text-stone-800 rounded px-2 py-1">target</code>, <code class="bg-stone-200 text-stone-800 rounded px-2 py-1">method</code></li>
                        </ul>
                    </div>
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Returns</h3>
                        <p>A list containing the trained `model` and `predictions`.</p>
                    </div>
                </div>
            </div>

            <div id="train_regular_model" class="content-section">
                <h2 class="text-3xl font-bold mb-4 text-stone-900">train_regular_model(...)</h2>
                 <div class="space-y-6 text-base text-stone-700 leading-relaxed">
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Purpose</h3>
                        <p>This function trains a machine learning model using the `caret` package, optimizing for "Accuracy" and *with* hyperparameter tuning, by calling `get_tune_grid` (assumed to be defined elsewhere) to determine the tuning parameters.</p>
                    </div>
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Arguments</h3>
                        <ul class="list-disc pl-5 space-y-2">
                            <li><code class="bg-stone-200 text-stone-800 rounded px-2 py-1">train_data</code>, <code class="bg-stone-200 text-stone-800 rounded px-2 py-1">test_data</code>, <code class="bg-stone-200 text-stone-800 rounded px-2 py-1">target</code>, <code class="bg-stone-200 text-stone-800 rounded px-2 py-1">method</code></li>
                        </ul>
                    </div>
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Returns</h3>
                        <p>A list containing the trained `model` and `predictions`.</p>
                    </div>
                </div>
            </div>
            
            <div id="train_lift_model_with_weights" class="content-section">
                 <h2 class="text-3xl font-bold mb-4 text-stone-900">train_lift_model_with_weights(...)</h2>
                 <div class="space-y-6 text-base text-stone-700 leading-relaxed">
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Purpose</h3>
                        <p>This function trains a machine learning model, optimizing for LIFT, and allows for the application of observation `weights` during training. It also includes hyperparameter tuning.</p>
                    </div>
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Arguments</h3>
                        <ul class="list-disc pl-5 space-y-2">
                             <li><code class="bg-stone-200 text-stone-800 rounded px-2 py-1">train_data</code>, <code class="bg-stone-200 text-stone-800 rounded px-2 py-1">test_data</code>, <code class="bg-stone-200 text-stone-800 rounded px-2 py-1">target</code>, <code class="bg-stone-200 text-stone-800 rounded px-2 py-1">method</code>, <code class="bg-stone-200 text-stone-800 rounded px-2 py-1">weights</code>, <code class="bg-stone-200 text-stone-800 rounded px-2 py-1">p</code></li>
                        </ul>
                    </div>
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Returns</h3>
                        <p>A list containing the trained `model` and `predictions`.</p>
                    </div>
                </div>
            </div>

            <div id="train_lift_model_withoutgrid_with_weights" class="content-section">
                <h2 class="text-3xl font-bold mb-4 text-stone-900">train_lift_model_withoutgrid_with_weights(...)</h2>
                <div class="space-y-6 text-base text-stone-700 leading-relaxed">
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Purpose</h3>
                        <p>Similar to `train_lift_model_with_weights`, but this function trains a LIFT-optimized model *without* explicit hyperparameter tuning, while still applying `weights`.</p>
                    </div>
                    <div>
                         <h3 class="text-xl font-semibold mb-2 text-sky-700">Arguments</h3>
                        <ul class="list-disc pl-5 space-y-2">
                             <li><code class="bg-stone-200 text-stone-800 rounded px-2 py-1">train_data</code>, <code class="bg-stone-200 text-stone-800 rounded px-2 py-1">test_data</code>, <code class="bg-stone-200 text-stone-800 rounded px-2 py-1">target</code>, <code class="bg-stone-200 text-stone-800 rounded px-2 py-1">method</code>, <code class="bg-stone-200 text-stone-800 rounded px-2 py-1">weights</code>, <code class="bg-stone-200 text-stone-800 rounded px-2 py-1">p</code></li>
                        </ul>
                    </div>
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Returns</h3>
                        <p>A list containing the trained `model` and `predictions`.</p>
                    </div>
                </div>
            </div>
            
            <div id="train_regular_model_with_weights" class="content-section">
                <h2 class="text-3xl font-bold mb-4 text-stone-900">train_regular_model_with_weights(...)</h2>
                <div class="space-y-6 text-base text-stone-700 leading-relaxed">
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Purpose</h3>
                        <p>This function trains a model optimizing for "Accuracy" with hyperparameter tuning and applies observation `weights` during training.</p>
                    </div>
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Arguments</h3>
                        <ul class="list-disc pl-5 space-y-2">
                            <li><code class="bg-stone-200 text-stone-800 rounded px-2 py-1">train_data</code>, <code class="bg-stone-200 text-stone-800 rounded px-2 py-1">test_data</code>, <code class="bg-stone-200 text-stone-800 rounded px-2 py-1">target</code>, <code class="bg-stone-200 text-stone-800 rounded px-2 py-1">method</code>, <code class="bg-stone-200 text-stone-800 rounded px-2 py-1">weights</code></li>
                        </ul>
                    </div>
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Returns</h3>
                        <p>A list containing the trained `model` and `predictions`.</p>
                    </div>
                </div>
            </div>

            <div id="train_regular_model_withoutgrid_with_weights" class="content-section">
                <h2 class="text-3xl font-bold mb-4 text-stone-900">train_regular_model_withoutgrid_with_weights(...)</h2>
                 <div class="space-y-6 text-base text-stone-700 leading-relaxed">
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Purpose</h3>
                        <p>This function trains a model optimizing for "Accuracy" *without* hyperparameter tuning but *with* observation `weights` applied during training.</p>
                    </div>
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Arguments</h3>
                        <ul class="list-disc pl-5 space-y-2">
                             <li><code class="bg-stone-200 text-stone-800 rounded px-2 py-1">train_data</code>, <code class="bg-stone-200 text-stone-800 rounded px-2 py-1">test_data</code>, <code class="bg-stone-200 text-stone-800 rounded px-2 py-1">target</code>, <code class="bg-stone-200 text-stone-800 rounded px-2 py-1">method</code>, <code class="bg-stone-200 text-stone-800 rounded px-2 py-1">weights</code></li>
                        </ul>
                    </div>
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Returns</h3>
                        <p>A list containing the trained `model` and `predictions`.</p>
                    </div>
                </div>
            </div>
            
            <div id="calculate_lift" class="content-section">
                <h2 class="text-3xl font-bold mb-4 text-stone-900">calculate_lift(data, p = 0.1)</h2>
                <div class="space-y-6 text-base text-stone-700 leading-relaxed">
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Purpose</h3>
                        <p>This is a custom helper function used by `get_train_control` to calculate the LIFT metric at a specified `p` percentage. It sorts the data by predicted probability and calculates how many actual positive cases are captured within the top `p` portion compared to a random selection.</p>
                    </div>
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Arguments</h3>
                        <ul class="list-disc pl-5 space-y-2">
                           <li><code class="bg-stone-200 text-stone-800 rounded px-2 py-1">data</code>: A data frame containing at least `Yes` (predicted probability for "Yes") and `obs` (actual class, "Yes" or "No") columns.</li>
                           <li><code class="bg-stone-200 text-stone-800 rounded px-2 py-1">p</code>: The percentage of the data to consider for the LIFT calculation.</li>
                        </ul>
                    </div>
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Returns</h3>
                        <p>A numeric value representing the LIFT at the specified `p` percentage.</p>
                    </div>
                </div>
            </div>

            <div id="plot_decision_tree" class="content-section">
                <h2 class="text-3xl font-bold mb-4 text-stone-900">plot_decision_tree(model)</h2>
                <div class="space-y-6 text-base text-stone-700 leading-relaxed">
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Purpose</h3>
                        <p>This function plots a decision tree model (specifically, an `rpart` object, often nested within a `caret` model's `finalModel` slot) and reports its total number of nodes, number of leaf nodes, and depth.</p>
                    </div>
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Arguments</h3>
                        <p><code class="bg-stone-200 text-stone-800 rounded px-2 py-1">model</code>: A trained model object, expected to have an `rpart` model in its `finalModel` slot.</p>
                    </div>
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Returns</h3>
                        <p>This function plots the tree and prints the node count, leaf count, and depth to the console. It does not return an R object.</p>
                    </div>
                </div>
            </div>

            <div id="generate_charts" class="content-section">
                <h2 class="text-3xl font-bold mb-4 text-stone-900">generate_charts(predictions, actual)</h2>
                <div class="space-y-6 text-base text-stone-700 leading-relaxed">
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Purpose</h3>
                        <p>This function generates various LIFT and Gains charts (cumulative and decile) based on predicted probabilities and actual outcomes. It uses the `gainslift` package for these visualizations.</p>
                    </div>
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Arguments</h3>
                         <ul class="list-disc pl-5 space-y-2">
                           <li><code class="bg-stone-200 text-stone-800 rounded px-2 py-1">predictions</code>: A numeric vector of predicted probabilities for the positive class.</li>
                           <li><code class="bg-stone-200 text-stone-800 rounded px-2 py-1">actual</code>: A vector of actual class labels ("Yes" or "No").</li>
                        </ul>
                    </div>
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Returns</h3>
                        <p>A list containing four chart objects: "Lift", "Decile Lift", "Gains", and "Decile Gains".</p>
                    </div>
                </div>
            </div>

            <div id="calculate_top_10_percent_lifts" class="content-section">
                <h2 class="text-3xl font-bold mb-4 text-stone-900">calculate_top_10_percent_lifts(predictions, actual)</h2>
                <div class="space-y-6 text-base text-stone-700 leading-relaxed">
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Purpose</h3>
                        <p>This function calculates the LIFT value specifically at the top 10% of the predictions.</p>
                    </div>
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Arguments</h3>
                        <ul class="list-disc pl-5 space-y-2">
                           <li><code class="bg-stone-200 text-stone-800 rounded px-2 py-1">predictions</code>: A numeric vector of predicted probabilities.</li>
                           <li><code class="bg-stone-200 text-stone-800 rounded px-2 py-1">actual</code>: A vector of actual class labels.</li>
                        </ul>
                    </div>
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Returns</h3>
                        <p>A list where each element represents the top 10% LIFT value for a dataset.</p>
                    </div>
                </div>
            </div>
            
             <div id="calculate_top_percent_lifts" class="content-section">
                <h2 class="text-3xl font-bold mb-4 text-stone-900">calculate_top_percent_lifts(predictions, actual, p = 0.1)</h2>
                <div class="space-y-6 text-base text-stone-700 leading-relaxed">
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Purpose</h3>
                        <p>A generalized version of `calculate_top_10_percent_lifts` that calculates the LIFT value at any specified top `p` percentage of the predictions.</p>
                    </div>
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Arguments</h3>
                        <ul class="list-disc pl-5 space-y-2">
                           <li><code class="bg-stone-200 text-stone-800 rounded px-2 py-1">predictions</code>, <code class="bg-stone-200 text-stone-800 rounded px-2 py-1">actual</code>, <code class="bg-stone-200 text-stone-800 rounded px-2 py-1">p</code> (optional)</li>
                        </ul>
                    </div>
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Returns</h3>
                        <p>A list where each element represents the top `p` percent LIFT value for a dataset.</p>
                    </div>
                </div>
            </div>

            <!-- Data.r functions -->
            <div id="prepare_kaggle_Churn_telo" class="content-section">
                <h2 class="text-3xl font-bold mb-4 text-stone-900">prepare_kaggle_Churn_telo(seed = 123)</h2>
                <div class="space-y-6 text-base text-stone-700 leading-relaxed">
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Purpose</h3>
                        <p>Prepares the Kaggle Telco Customer Churn dataset for modeling. It performs data cleaning, feature engineering, scaling, dummy variable creation, and splits the data into training and test sets using a simple random split.</p>
                    </div>
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Arguments</h3>
                        <p><code class="bg-stone-200 text-stone-800 rounded px-2 py-1">seed</code> (Optional): An integer for setting the random seed for reproducibility. Defaults to 123.</p>
                    </div>
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Returns</h3>
                        <p>A list containing `train`, `test`, and `final` datasets.</p>
                    </div>
                </div>
            </div>

            <div id="prepare_kaggle_Churn_telo_with_stratified" class="content-section">
                <h2 class="text-3xl font-bold mb-4 text-stone-900">prepare_kaggle_Churn_telo_with_stratified(seed = 123)</h2>
                 <div class="space-y-6 text-base text-stone-700 leading-relaxed">
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Purpose</h3>
                        <p>Similar to the above, but uses `createDataPartition` for a *stratified* split of the data, ensuring the proportion of the target variable is maintained in both training and test sets.</p>
                    </div>
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Arguments</h3>
                        <p><code class="bg-stone-200 text-stone-800 rounded px-2 py-1">seed</code> (Optional): An integer for setting the random seed. Defaults to 123.</p>
                    </div>
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Returns</h3>
                        <p>A list containing `train`, `test`, and `final` datasets.</p>
                    </div>
                </div>
            </div>

            <div id="prepare_bank_dataset" class="content-section">
                <h2 class="text-3xl font-bold mb-4 text-stone-900">prepare_bank_dataset(seed = 123)</h2>
                 <div class="space-y-6 text-base text-stone-700 leading-relaxed">
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Purpose</h3>
                        <p>Prepares a bank marketing dataset. It converts columns to factors, renames target variable levels, and splits data into training and test sets using a simple random sample.</p>
                    </div>
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Arguments</h3>
                        <p><code class="bg-stone-200 text-stone-800 rounded px-2 py-1">seed</code> (Optional): An integer for the random seed. Defaults to 123.</p>
                    </div>
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Returns</h3>
                        <p>A list containing `train`, `test`, `actual` (numeric target from test), and `final` datasets.</p>
                    </div>
                </div>
            </div>

            <div id="prepare_bank_dataset_with_stratified" class="content-section">
                <h2 class="text-3xl font-bold mb-4 text-stone-900">prepare_bank_dataset_with_stratified(seed = 123)</h2>
                <div class="space-y-6 text-base text-stone-700 leading-relaxed">
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Purpose</h3>
                        <p>Similar to `prepare_bank_dataset`, but uses `createDataPartition` for a *stratified* split to preserve the class distribution of the target variable.</p>
                    </div>
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Arguments</h3>
                        <p><code class="bg-stone-200 text-stone-800 rounded px-2 py-1">seed</code> (Optional): An integer for the random seed. Defaults to 123.</p>
                    </div>
                     <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Returns</h3>
                        <p>A list containing `train`, `test`, `actual`, and `final` datasets.</p>
                    </div>
                </div>
            </div>

            <div id="prepare_credit_data" class="content-section">
                <h2 class="text-3xl font-bold mb-4 text-stone-900">prepare_credit_data(seed = 123)</h2>
                <div class="space-y-6 text-base text-stone-700 leading-relaxed">
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Purpose</h3>
                        <p>Prepares a credit risk dataset. It converts the target variable to a factor and splits the data into training and test sets using a simple random sample.</p>
                    </div>
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Arguments</h3>
                        <p><code class="bg-stone-200 text-stone-800 rounded px-2 py-1">seed</code> (Optional): An integer for the random seed. Defaults to 123.</p>
                    </div>
                    <div>
                        <h3 class="text-xl font-semibold mb-2 text-sky-700">Returns</h3>
                        <p>A list containing `train`, `test`, `actual`, and `final` datasets.</p>
                    </div>
                </div>
            </div>

        </main>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const navLinks = document.querySelectorAll('.nav-link');
            const contentSections = document.querySelectorAll('.content-section');
            const categoryHeaders = document.querySelectorAll('.nav-category-header');

            navLinks.forEach(link => {
                link.addEventListener('click', function(e) {
                    e.preventDefault();
                    
                    const targetId = this.getAttribute('data-target');
                    
                    // Update content
                    contentSections.forEach(section => {
                        section.classList.remove('active');
                    });
                    document.getElementById(targetId).classList.add('active');
                    
                    // Update active link style
                    navLinks.forEach(nav => nav.classList.remove('active'));
                    this.classList.add('active');
                });
            });

            categoryHeaders.forEach(header => {
                header.addEventListener('click', function() {
                    this.parentElement.classList.toggle('collapsed');
                });
            });

            // Activate the first function by default if you want a function to be displayed on load
            // For example, to show 'get_train_control':
            // const firstLink = document.querySelector('.nav-link');
            // if (firstLink) {
            //     firstLink.click();
            // }
        });
    </script>
</body>
</html>
