<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ultimate Flange | Industrial Precision Solutions</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://unpkg.com/@google/model-viewer/dist/model-viewer.min.js" type="module"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary-blue: #1e40af;
            --secondary-blue: #3b82f6;
            --accent-blue: #60a5fa;
        }
        
        body {
            font-family: 'Inter', sans-serif;
            scroll-behavior: smooth;
            overflow-x: hidden;
        }
        
        .glass-nav {
            background: rgba(255, 255, 255, 0.92);
            backdrop-filter: blur(12px);
            border-bottom: 1px solid rgba(0, 0, 0, 0.08);
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.05);
        }
        
        .gradient-text {
            background: linear-gradient(135deg, #1e40af 0%, #3b82f6 50%, #60a5fa 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        
        .hero-gradient {
            background: linear-gradient(135deg, rgba(30, 64, 175, 0.05) 0%, rgba(59, 130, 246, 0.05) 100%);
        }
        
        /* Enhanced Animations */
        .reveal {
            opacity: 0;
            transform: translateY(40px);
            transition: all 0.8s cubic-bezier(0.22, 1, 0.36, 1);
        }
        
        .reveal.active {
            opacity: 1;
            transform: translateY(0);
        }
        
        .stagger-delay-1 { transition-delay: 0.1s; }
        .stagger-delay-2 { transition-delay: 0.2s; }
        .stagger-delay-3 { transition-delay: 0.3s; }
        .stagger-delay-4 { transition-delay: 0.4s; }
        
        /* Auth Overlay */
        #auth-overlay {
            z-index: 9999;
        }
        
        /* Loading Animation */
        .loading-shimmer {
            position: fixed;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(37, 99, 235, 0.8), transparent);
            z-index: 2000;
            transition: left 1.2s cubic-bezier(0.65, 0, 0.35, 1);
        }
        
        /* Enhanced Chip Styles */
        .flange-chip {
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            cursor: pointer;
            white-space: nowrap;
        }
        
        .flange-chip.active {
            background-color: var(--primary-blue);
            color: white;
            border-color: var(--primary-blue);
            box-shadow: 0 6px 20px rgba(37, 99, 235, 0.25);
            transform: translateY(-2px);
        }
        
        .no-scrollbar::-webkit-scrollbar {
            display: none;
        }
        
        .no-scrollbar {
            -ms-overflow-style: none;
            scrollbar-width: none;
        }
        
        /* Enhanced Cards */
        .feature-card {
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            background: white;
            border: 1px solid rgba(226, 232, 240, 0.9);
        }
        
        .feature-card:hover {
            border-color: var(--secondary-blue);
            transform: translateY(-8px);
            box-shadow: 0 20px 40px -15px rgba(0, 0, 0, 0.1);
        }
        
        .knowledge-card {
            transition: all 0.3s ease;
            background: white;
            border: 1px solid rgba(226, 232, 240, 0.8);
        }
        
        .knowledge-card:hover {
            border-color: var(--secondary-blue);
            transform: translateY(-5px);
            box-shadow: 0 20px 40px -10px rgba(0, 0, 0, 0.08);
        }
        
        /* 3D Viewer Styles */
        .model-viewer-container {
            width: 100%;
            height: 400px;
            border-radius: 16px;
            overflow: hidden;
            background: linear-gradient(135deg, #f8fafc 0%, #e2e8f0 100%);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
            position: relative;
        }
        
        /* 3D Viewer Controls */
        .model-controls {
            position: absolute;
            bottom: 16px;
            left: 16px;
            right: 16px;
            display: flex;
            gap: 8px;
            justify-content: center;
            z-index: 10;
        }
        
        .model-control-btn {
            background: rgba(30, 64, 175, 0.85);
            color: white;
            border: none;
            padding: 8px 16px;
            border-radius: 8px;
            font-size: 14px;
            font-weight: 600;
            cursor: pointer;
            backdrop-filter: blur(10px);
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 6px;
        }
        
        .model-control-btn:hover {
            background: rgba(30, 64, 175, 1);
            transform: translateY(-2px);
        }
        
        model-viewer {
            --poster-color: transparent;
            --progress-bar-color: #3b82f6;
            --progress-bar-height: 3px;
            --progress-mask: none;
        }
        
        .ar-button {
            position: absolute;
            bottom: 16px;
            right: 16px;
            background: rgba(30, 64, 175, 0.9);
            color: white;
            border: none;
            padding: 8px 16px;
            border-radius: 8px;
            font-size: 14px;
            font-weight: 600;
            cursor: pointer;
            backdrop-filter: blur(10px);
            transition: all 0.3s ease;
        }
        
        .ar-button:hover {
            background: rgba(30, 64, 175, 1);
            transform: translateY(-2px);
        }
        
        /* Loading state for 3D viewer */
        .model-viewer-container.loading::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, #f0f4f8 25%, #e2e8f0 50%, #f0f4f8 75%);
            background-size: 200% 100%;
            animation: loadingShimmer 1.5s infinite;
            z-index: 1;
        }
        
        @keyframes loadingShimmer {
            0% { background-position: -200% 0; }
            100% { background-position: 200% 0; }
        }
        
        /* 3D Controls */
        .rotation-control {
            position: absolute;
            top: 16px;
            left: 16px;
            background: rgba(255, 255, 255, 0.9);
            padding: 12px;
            border-radius: 12px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
            z-index: 10;
            width: 200px;
        }
        
        .rotation-control label {
            display: block;
            font-size: 12px;
            font-weight: 600;
            color: #374151;
            margin-bottom: 8px;
        }
        
        .rotation-control input[type="range"] {
            width: 100%;
            height: 4px;
            background: #e5e7eb;
            border-radius: 2px;
            outline: none;
        }
        
        .rotation-control input[type="range"]::-webkit-slider-thumb {
            appearance: none;
            width: 16px;
            height: 16px;
            background: #3b82f6;
            border-radius: 50%;
            cursor: pointer;
            border: 2px solid white;
            box-shadow: 0 2px 6px rgba(0,0,0,0.2);
        }
        
        /* Enhanced Search */
        .search-container {
            transition: all 0.3s ease;
        }
        
        .search-container:focus-within {
            box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.15);
            border-color: var(--secondary-blue);
        }
        
        /* Hidden content until login */
        #main-content {
            filter: blur(8px);
            pointer-events: none;
            transition: filter 0.5s ease;
        }
        
        body.authenticated #main-content {
            filter: blur(0);
            pointer-events: auto;
        }
        
        /* Enhanced Table */
        .spec-table {
            border-collapse: separate;
            border-spacing: 0;
        }
        
        .spec-table th {
            background: rgba(30, 64, 175, 0.1);
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 0.05em;
        }
        
        .spec-table tr:hover td {
            background: rgba(59, 130, 246, 0.03);
        }
        
        /* Contact Form */
        .contact-form input:focus,
        .contact-form textarea:focus,
        .contact-form select:focus {
            box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.15);
            border-color: var(--secondary-blue);
        }
        
        /* Stats Counter */
        .stat-card {
            background: white;
            border-radius: 16px;
            padding: 2rem;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
            transition: transform 0.3s ease;
        }
        
        .stat-card:hover {
            transform: translateY(-5px);
        }
        
        /* Mobile Menu */
        .mobile-menu {
            transform: translateX(100%);
            transition: transform 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }
        
        .mobile-menu.active {
            transform: translateX(0);
        }
        
        /* Order Modal Styles */
        #order-modal .hidden {
            display: none !important;
        }
        
        #order-modal .bg-green-500 {
            background-color: #10b981;
        }
        
        #order-modal .bg-green-600 {
            background-color: #059669;
        }
        
        #order-modal .bg-green-700 {
            background-color: #047857;
        }
        
        #order-modal .bg-green-800 {
            background-color: #065f46;
        }
        
        /* Step indicators */
        .step-indicator {
            width: 10px;
            height: 10px;
            border-radius: 50%;
            background-color: #e5e7eb;
            transition: all 0.3s ease;
        }
        
        .step-indicator.active {
            background-color: #3b82f6;
            transform: scale(1.2);
        }
        
        .step-indicator.completed {
            background-color: #10b981;
        }
        
        /* 3D Model Thumbnails */
        .model-thumbnail {
            width: 100%;
            height: 180px;
            border-radius: 12px;
            overflow: hidden;
            background: linear-gradient(135deg, #f1f5f9 0%, #e2e8f0 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.3s ease;
            cursor: pointer;
        }
        
        .model-thumbnail:hover {
            transform: translateY(-4px);
            box-shadow: 0 12px 24px rgba(0, 0, 0, 0.1);
        }
        
        .model-thumbnail img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        
        .model-placeholder {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            color: #64748b;
        }
        
        .model-placeholder i {
            font-size: 48px;
            margin-bottom: 12px;
            color: #94a3b8;
        }
    </style>
</head>
<body class="bg-slate-50 text-slate-900">

    <div id="transition-loader" class="loading-shimmer"></div>

    <!-- Login/Signup Modal Overlay -->
    <div id="auth-overlay" class="fixed inset-0 bg-slate-900/70 backdrop-blur-lg flex items-center justify-center p-4 z-50">
        <div class="bg-white w-full max-w-md rounded-3xl shadow-2xl overflow-hidden p-8 relative">
            <button onclick="closeAuth()" class="absolute top-4 right-4 text-slate-400 hover:text-slate-700">
                <i class="fas fa-times text-xl"></i>
            </button>
            
            <div id="login-form">
                <div class="text-center mb-8">
                    <div class="bg-gradient-to-br from-blue-600 to-blue-800 w-20 h-20 rounded-2xl flex items-center justify-center mx-auto mb-6 shadow-xl">
                        <i class="fas fa-industry text-white text-3xl"></i>
                    </div>
                    <h2 class="text-3xl font-bold text-slate-900">Portal Access</h2>
                    <p class="text-slate-500 mt-2">Sign in to access technical data and pricing</p>
                </div>
                <form class="space-y-5" onsubmit="handleAuth(event, 'partner')">
                    <div>
                        <label class="block text-sm font-semibold text-slate-700 mb-2">Email Address</label>
                        <input type="email" id="login-email" required placeholder="name@company.com" 
                               class="w-full px-5 py-3.5 rounded-xl border-2 border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none transition">
                    </div>
                    <div>
                        <label class="block text-sm font-semibold text-slate-700 mb-2">Password</label>
                        <input type="password" required placeholder="••••••••" 
                               class="w-full px-5 py-3.5 rounded-xl border-2 border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none transition">
                    </div>
                    <div class="flex items-center justify-between">
                        <label class="flex items-center">
                            <input type="checkbox" class="rounded border-slate-300 text-blue-600 focus:ring-blue-500">
                            <span class="ml-2 text-sm text-slate-600">Remember me</span>
                        </label>
                        <a href="#" class="text-sm text-blue-600 font-medium hover:text-blue-800">Forgot password?</a>
                    </div>
                    <button type="submit" 
                            class="w-full py-4 bg-gradient-to-r from-blue-600 to-blue-800 text-white font-bold rounded-xl hover:from-blue-700 hover:to-blue-900 transition-all transform hover:-translate-y-1 active:scale-95 shadow-lg shadow-blue-100 hover:shadow-xl">
                        <i class="fas fa-sign-in-alt mr-2"></i>Login to Portal
                    </button>
                    
                    <div class="relative flex py-4 items-center">
                        <div class="flex-grow border-t border-slate-100"></div>
                        <span class="flex-shrink mx-4 text-slate-400 text-xs font-bold uppercase tracking-widest">or</span>
                        <div class="flex-grow border-t border-slate-100"></div>
                    </div>

                    <button type="button" onclick="handleAuth(event, 'visitor')" 
                            class="w-full py-3.5 bg-white border-2 border-slate-100 text-slate-700 font-bold rounded-xl hover:border-blue-200 hover:text-blue-600 transition-all flex items-center justify-center gap-3 group">
                        <i class="fas fa-user text-slate-400 group-hover:text-blue-500"></i>
                        <span>Continue as Visitor</span>
                        <i class="fas fa-arrow-right text-sm group-hover:translate-x-1 transition-transform"></i>
                    </button>

                    <p class="text-center text-sm text-slate-500 mt-8">
                        Don't have access? <button type="button" onclick="toggleAuthView('signup')" 
                        class="text-blue-600 font-semibold hover:text-blue-800 hover:underline">Request Account</button>
                    </p>
                </form>
            </div>

            <div id="signup-form" class="hidden">
                <div class="text-center mb-8">
                    <h2 class="text-3xl font-bold text-slate-900">Create Partner Account</h2>
                    <p class="text-slate-500 mt-2">Join our industrial network for exclusive access</p>
                </div>
                <form class="space-y-5" onsubmit="handleAuth(event, 'partner')">
                    <div class="grid grid-cols-2 gap-4">
                        <div>
                            <label class="block text-sm font-semibold text-slate-700 mb-2">First Name</label>
                            <input type="text" required 
                                   class="w-full px-4 py-3 rounded-xl border-2 border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none transition">
                        </div>
                        <div>
                            <label class="block text-sm font-semibold text-slate-700 mb-2">Last Name</label>
                            <input type="text" required 
                                   class="w-full px-4 py-3 rounded-xl border-2 border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none transition">
                        </div>
                    </div>
                    <div>
                        <label class="block text-sm font-semibold text-slate-700 mb-2">Email</label>
                        <input type="email" required 
                               class="w-full px-4 py-3 rounded-xl border-2 border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none transition">
                    </div>
                    <div>
                        <label class="block text-sm font-semibold text-slate-700 mb-2">Company</label>
                        <input type="text" required 
                               class="w-full px-4 py-3 rounded-xl border-2 border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none transition">
                    </div>
                    <div>
                        <label class="block text-sm font-semibold text-slate-700 mb-2">Industry</label>
                        <select class="w-full px-4 py-3 rounded-xl border-2 border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none transition">
                            <option value="">Select Industry</option>
                            <option value="oil_gas">Oil & Gas</option>
                            <option value="chemical">Chemical Processing</option>
                            <option value="power">Power Generation</option>
                            <option value="marine">Marine & Offshore</option>
                            <option value="construction">Construction</option>
                            <option value="other">Other</option>
                        </select>
                    </div>
                    <button type="submit" 
                            class="w-full py-4 bg-gradient-to-r from-blue-600 to-blue-800 text-white font-bold rounded-xl hover:from-blue-700 hover:to-blue-900 transition-all shadow-lg shadow-blue-100">
                        <i class="fas fa-user-plus mr-2"></i>Create Partner Profile
                    </button>
                    <p class="text-center text-sm text-slate-500 mt-8">
                        Already have an account? <button type="button" onclick="toggleAuthView('login')" 
                        class="text-blue-600 font-semibold hover:text-blue-800 hover:underline">Sign In</button>
                    </p>
                </form>
            </div>
        </div>
    </div>

    <!-- Order Process Modal -->
    <div id="order-modal" class="fixed inset-0 bg-black/60 backdrop-blur-md hidden items-center justify-center p-4 z-50">
        <div class="bg-white w-full max-w-2xl rounded-3xl shadow-2xl overflow-hidden relative">
            <button onclick="closeOrderModal()" class="absolute top-4 right-4 text-slate-400 hover:text-slate-700 z-10">
                <i class="fas fa-times text-2xl"></i>
            </button>
            
            <!-- Step Indicators -->
            <div class="px-8 pt-8">
                <div class="flex items-center justify-between mb-8">
                    <div class="flex items-center gap-4">
                        <div id="step-indicator-1" class="step-indicator w-10 h-10 rounded-full bg-blue-600 text-white flex items-center justify-center font-bold active">1</div>
                        <div id="step-indicator-2" class="step-indicator w-10 h-10 rounded-full bg-slate-200 text-slate-500 flex items-center justify-center font-bold">2</div>
                        <div id="step-indicator-3" class="step-indicator w-10 h-10 rounded-full bg-slate-200 text-slate-500 flex items-center justify-center font-bold">3</div>
                        <div id="step-indicator-4" class="step-indicator w-10 h-10 rounded-full bg-slate-200 text-slate-500 flex items-center justify-center font-bold">4</div>
                    </div>
                    <div class="text-sm font-semibold text-slate-700">
                        Step <span id="current-step">1</span> of 4
                    </div>
                </div>
            </div>
            
            <!-- Step 1: Product Selection -->
            <div id="order-step-1" class="p-8">
                <div class="text-center mb-8">
                    <h2 class="text-3xl font-bold text-slate-900">Order Request - Step 1</h2>
                    <p class="text-slate-600 mt-2">Select product and specifications</p>
                </div>
                
                <form class="space-y-5">
                    <div>
                        <label class="block text-sm font-semibold text-slate-700 mb-2">Product *</label>
                        <select id="order-product" class="w-full px-4 py-3 rounded-xl border-2 border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none transition">
                            <option value="">Select Product</option>
                            <option value="wnf">Weld Neck Flange</option>
                            <option value="lwn">Long Weld Neck Flange</option>
                            <option value="slipon">Slip-On Flange</option>
                            <option value="blind">Blind Flange</option>
                            <option value="puddle">Puddle Flange</option>
                            <option value="plasma">Plasma CNC Cutting</option>
                            <option value="profile">Profile Cutting Services</option>
                            <option value="custom">Custom Requirements</option>
                        </select>
                    </div>
                    
                    <div class="grid md:grid-cols-2 gap-5">
                        <div>
                            <label class="block text-sm font-semibold text-slate-700 mb-2">Quantity *</label>
                            <input type="number" min="1" value="1" id="order-quantity" class="w-full px-4 py-3 rounded-xl border-2 border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none transition">
                        </div>
                        <div>
                            <label class="block text-sm font-semibold text-slate-700 mb-2">Size / Dimensions *</label>
                            <input type="text" id="order-size" placeholder="e.g., 10-inch, DN250" class="w-full px-4 py-3 rounded-xl border-2 border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none transition">
                        </div>
                    </div>
                    
                    <div>
                        <label class="block text-sm font-semibold text-slate-700 mb-2">Material Specification *</label>
                        <select id="order-material" class="w-full px-4 py-3 rounded-xl border-2 border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none transition">
                            <option value="">Select Material</option>
                            <option value="carbon">Carbon Steel (A105)</option>
                            <option value="stainless">Stainless Steel 316</option>
                            <option value="alloy">Alloy Steel</option>
                            <option value="duplex">Duplex Stainless</option>
                            <option value="custom">Custom Material</option>
                        </select>
                    </div>
                    
                    <div>
                        <label class="block text-sm font-semibold text-slate-700 mb-2">Additional Specifications</label>
                        <textarea rows="3" id="order-specs" class="w-full px-4 py-3 rounded-xl border-2 border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none transition" placeholder="Pressure rating, surface finish, coating, etc."></textarea>
                    </div>
                    
                    <button type="button" onclick="nextOrderStep(2)" class="w-full py-4 bg-gradient-to-r from-blue-600 to-blue-800 text-white font-bold rounded-xl hover:from-blue-700 hover:to-blue-900 transition-all shadow-lg">
                        Next: Contact Details <i class="fas fa-arrow-right ml-2"></i>
                    </button>
                </form>
            </div>
            
            <!-- Step 2: Contact & Delivery -->
            <div id="order-step-2" class="p-8 hidden">
                <div class="text-center mb-8">
                    <h2 class="text-3xl font-bold text-slate-900">Order Request - Step 2</h2>
                    <p class="text-slate-600 mt-2">Your contact and delivery information</p>
                </div>
                
                <form class="space-y-5">
                    <div class="grid md:grid-cols-2 gap-5">
                        <div>
                            <label class="block text-sm font-semibold text-slate-700 mb-2">First Name *</label>
                            <input type="text" id="order-firstname" required class="w-full px-4 py-3 rounded-xl border-2 border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none transition">
                        </div>
                        <div>
                            <label class="block text-sm font-semibold text-slate-700 mb-2">Last Name *</label>
                            <input type="text" id="order-lastname" required class="w-full px-4 py-3 rounded-xl border-2 border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none transition">
                        </div>
                    </div>
                    
                    <div class="grid md:grid-cols-2 gap-5">
                        <div>
                            <label class="block text-sm font-semibold text-slate-700 mb-2">Email *</label>
                            <input type="email" id="order-email" required class="w-full px-4 py-3 rounded-xl border-2 border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none transition">
                        </div>
                        <div>
                            <label class="block text-sm font-semibold text-slate-700 mb-2">Phone *</label>
                            <input type="tel" id="order-phone" required class="w-full px-4 py-3 rounded-xl border-2 border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none transition">
                        </div>
                    </div>
                    
                    <div>
                        <label class="block text-sm font-semibold text-slate-700 mb-2">Company *</label>
                        <input type="text" id="order-company" required class="w-full px-4 py-3 rounded-xl border-2 border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none transition">
                    </div>
                    
                    <div>
                        <label class="block text-sm font-semibold text-slate-700 mb-2">Delivery Address</label>
                        <textarea rows="3" id="order-address" class="w-full px-4 py-3 rounded-xl border-2 border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none transition" placeholder="Full address for delivery"></textarea>
                    </div>
                    
                    <div>
                        <label class="block text-sm font-semibold text-slate-700 mb-2">Preferred Contact Method</label>
                        <div class="flex gap-4 mt-2">
                            <label class="flex items-center">
                                <input type="radio" name="contactMethod" value="email" checked class="mr-2">
                                <span class="text-slate-700">Email</span>
                            </label>
                            <label class="flex items-center">
                                <input type="radio" name="contactMethod" value="phone" class="mr-2">
                                <span class="text-slate-700">Phone</span>
                            </label>
                            <label class="flex items-center">
                                <input type="radio" name="contactMethod" value="whatsapp" class="mr-2">
                                <span class="text-slate-700">WhatsApp</span>
                            </label>
                        </div>
                    </div>
                    
                    <div class="flex gap-4">
                        <button type="button" onclick="prevOrderStep(1)" class="flex-1 py-3.5 bg-slate-200 text-slate-700 font-bold rounded-xl hover:bg-slate-300 transition">
                            <i class="fas fa-arrow-left mr-2"></i>Back
                        </button>
                        <button type="button" onclick="nextOrderStep(3)" class="flex-1 py-3.5 bg-gradient-to-r from-blue-600 to-blue-800 text-white font-bold rounded-xl hover:from-blue-700 hover:to-blue-900 transition">
                            Next: Review <i class="fas fa-arrow-right ml-2"></i>
                        </button>
                    </div>
                </form>
            </div>
            
            <!-- Step 3: Review & Submit -->
            <div id="order-step-3" class="p-8 hidden">
                <div class="text-center mb-8">
                    <h2 class="text-3xl font-bold text-slate-900">Review & Submit</h2>
                    <p class="text-slate-600 mt-2">Confirm your order request details</p>
                </div>
                
                <div class="bg-slate-50 rounded-2xl p-6 mb-6">
                    <h4 class="font-bold text-slate-800 mb-4">Order Summary</h4>
                    <div class="space-y-3">
                        <div class="flex justify-between">
                            <span class="text-slate-600">Product:</span>
                            <span class="font-semibold" id="review-product">-</span>
                        </div>
                        <div class="flex justify-between">
                            <span class="text-slate-600">Quantity:</span>
                            <span class="font-semibold" id="review-quantity">-</span>
                        </div>
                        <div class="flex justify-between">
                            <span class="text-slate-600">Material:</span>
                            <span class="font-semibold" id="review-material">-</span>
                        </div>
                        <div class="flex justify-between">
                            <span class="text-slate-600">Contact Method:</span>
                            <span class="font-semibold" id="review-contact">-</span>
                        </div>
                        <div class="flex justify-between">
                            <span class="text-slate-600">Response Time:</span>
                            <span class="font-semibold text-green-600">Within 24 hours</span>
                        </div>
                    </div>
                </div>
                
                <div class="bg-blue-50 rounded-2xl p-6 mb-6">
                    <h4 class="font-bold text-blue-800 mb-2 flex items-center gap-2">
                        <i class="fas fa-info-circle"></i>What happens next?
                    </h4>
                    <p class="text-blue-700 text-sm">
                        1. Your quotation request is sent <strong>directly to our supplier team</strong><br>
                        2. Supplier will contact you via your preferred method<br>
                        3. You'll receive <strong>pricing, delivery expectations, and invoice</strong><br>
                        4. Finalize order and schedule production/delivery
                    </p>
                </div>
                
                <div class="flex gap-4">
                    <button type="button" onclick="prevOrderStep(2)" class="flex-1 py-3.5 bg-slate-200 text-slate-700 font-bold rounded-xl hover:bg-slate-300 transition">
                        <i class="fas fa-arrow-left mr-2"></i>Back
                    </button>
                    <button type="button" onclick="submitOrder()" class="flex-1 py-3.5 bg-gradient-to-r from-green-600 to-green-800 text-white font-bold rounded-xl hover:from-green-700 hover:to-green-900 transition shadow-lg">
                        <i class="fas fa-paper-plane mr-2"></i>Submit to Supplier
                    </button>
                </div>
            </div>
            
            <!-- Step 4: Confirmation -->
            <div id="order-step-4" class="p-8 hidden">
                <div class="text-center py-8">
                    <div class="w-20 h-20 bg-green-100 rounded-full flex items-center justify-center mx-auto mb-6">
                        <i class="fas fa-check text-green-600 text-3xl"></i>
                    </div>
                    <h2 class="text-3xl font-bold text-slate-900 mb-4">Request Sent to Supplier!</h2>
                    
                    <div class="bg-slate-50 rounded-2xl p-6 mb-6">
                        <p class="text-slate-700 mb-4">
                            <strong>Your quotation request has been sent directly to our supplier team.</strong>
                        </p>
                        <p class="text-slate-600 text-sm">
                            <i class="fas fa-envelope text-blue-500 mr-2"></i>
                            Supplier will contact you within <strong>24 hours</strong> with:
                        </p>
                        <ul class="text-slate-600 text-sm mt-3 space-y-2">
                            <li class="flex items-center gap-2"><i class="fas fa-rupee-sign text-green-500"></i>Detailed pricing and quotation</li>
                            <li class="flex items-center gap-2"><i class="fas fa-truck text-blue-500"></i>Delivery timeline and expectations</li>
                            <li class="flex items-center gap-2"><i class="fas fa-file-invoice-dollar text-purple-500"></i>Proforma invoice for approval</li>
                        </ul>
                    </div>
                    
                    <div class="text-sm text-slate-500 mb-6">
                        Order Reference: <strong id="order-reference">UF-ORD-${Date.now().toString().slice(-6)}</strong>
                    </div>
                    
                    <div class="bg-yellow-50 border border-yellow-200 rounded-xl p-4 mb-6">
                        <p class="text-sm text-yellow-800">
                            <i class="fas fa-exclamation-circle mr-2"></i>
                            <strong>Note:</strong> The supplier will contact you directly via the email/phone you provided.
                        </p>
                    </div>
                    
                    <button onclick="closeOrderModal()" class="w-full py-3.5 bg-gradient-to-r from-blue-600 to-blue-800 text-white font-bold rounded-xl hover:from-blue-700 hover:to-blue-900 transition">
                        <i class="fas fa-home mr-2"></i>Return to Home
                    </button>
                </div>
            </div>
        </div>
    </div>

    <!-- Mobile Menu -->
    <div id="mobile-menu" class="mobile-menu fixed inset-y-0 right-0 w-64 bg-white shadow-2xl z-50 p-6">
        <div class="flex justify-between items-center mb-8">
            <span class="text-xl font-bold text-blue-600">UltimateFlange</span>
            <button onclick="toggleMobileMenu()" class="text-slate-500 hover:text-slate-800">
                <i class="fas fa-times text-xl"></i>
            </button>
        </div>
        <div class="space-y-6">
            <a href="#home" onclick="toggleMobileMenu()" class="block text-slate-700 hover:text-blue-600 font-medium py-2">Home</a>
            <a href="#products" onclick="toggleMobileMenu()" class="block text-slate-700 hover:text-blue-600 font-medium py-2">Products</a>
            <a href="#specifications" onclick="toggleMobileMenu()" class="block text-slate-700 hover:text-blue-600 font-medium py-2">Specifications</a>
            <a href="#about" onclick="toggleMobileMenu()" class="block text-slate-700 hover:text-blue-600 font-medium py-2">Know More</a>
            <a href="#contact" onclick="toggleMobileMenu()" class="block text-slate-700 hover:text-blue-600 font-medium py-2">Contact</a>
            <div class="pt-4 border-t">
                <div id="mobile-user-status" class="px-3 py-2 bg-slate-100 rounded-lg text-sm font-bold text-slate-600 mb-4">Partner</div>
                <button onclick="logout()" class="w-full text-left text-slate-500 hover:text-red-600 font-medium py-2">
                    <i class="fas fa-sign-out-alt mr-2"></i>Logout
                </button>
            </div>
        </div>
    </div>

    <div id="main-content">
        <!-- Enhanced Navigation -->
        <nav class="fixed top-0 w-full z-40 glass-nav">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="flex justify-between h-20 items-center">
                    <div class="flex items-center gap-3">
                        <div class="w-10 h-10 bg-gradient-to-br from-blue-600 to-blue-800 rounded-xl flex items-center justify-center shadow-md">
                            <i class="fas fa-cogs text-white text-lg"></i>
                        </div>
                        <div>
                            <span class="text-xl font-bold text-slate-900 tracking-tight">UltimateFlange</span>
                            <span class="block text-xs text-slate-500 font-medium">Industrial Solutions</span>
                        </div>
                    </div>
                    
                    <!-- Desktop Navigation -->
                    <div class="hidden lg:flex space-x-8 font-medium text-sm items-center">
                        <a href="#home" class="hover:text-blue-600 transition text-slate-700 font-medium">Home</a>
                        <a href="#products" class="hover:text-blue-600 transition text-slate-700 font-medium">Products</a>
                        <a href="#specifications" class="hover:text-blue-600 transition text-slate-700 font-medium">Specifications</a>
                        <a href="#about" class="hover:text-blue-600 transition text-slate-700 font-medium">Know More</a>
                        <a href="#contact" class="hover:text-blue-600 transition text-slate-700 font-medium">Contact</a>
                        
                        <div class="flex items-center gap-4">
                            <div id="user-status" class="px-3 py-1.5 bg-blue-50 rounded-full text-xs font-bold text-blue-600 uppercase border border-blue-100">
                                <i class="fas fa-user-shield mr-1"></i>Partner
                            </div>
                            <button onclick="logout()" class="text-slate-400 hover:text-red-600 transition text-xs font-bold uppercase tracking-wider">
                                <i class="fas fa-sign-out-alt mr-1"></i>Logout
                            </button>
                            <button onclick="openOrderModal()" class="px-5 py-2.5 bg-gradient-to-r from-blue-600 to-blue-800 text-white font-semibold rounded-lg hover:from-blue-700 hover:to-blue-900 transition shadow-md">
                                <i class="fas fa-file-invoice-dollar mr-2"></i>Order Now
                            </button>
                        </div>
                    </div>
                    
                    <!-- Mobile Menu Button -->
                    <button onclick="toggleMobileMenu()" class="lg:hidden text-slate-700 hover:text-blue-600">
                        <i class="fas fa-bars text-xl"></i>
                    </button>
                </div>
            </div>
        </nav>

        <!-- Enhanced Hero Section -->
        <section id="home" class="pt-32 pb-20 px-4 reveal hero-gradient">
            <div class="max-w-7xl mx-auto">
                <div class="flex flex-col lg:flex-row items-center gap-12 lg:gap-16">
                    <div class="flex-1 space-y-8">
                        <div class="space-y-4">
                            <span class="inline-block px-4 py-1.5 bg-blue-100 text-blue-700 rounded-full text-sm font-bold uppercase tracking-widest">
                                <i class="fas fa-award mr-2"></i>Industry Leader
                            </span>
                            <h1 class="text-5xl lg:text-7xl font-bold leading-tight">
                                Precision <span class="gradient-text">Industrial</span> Solutions
                            </h1>
                            <p class="text-xl text-slate-600 max-w-2xl leading-relaxed">
                                Setting the global standard for high-pressure flanges, precision metal cutting, and industrial components. Durability, accuracy, and reliability delivered worldwide.
                            </p>
                        </div>
                        
                        <div class="flex flex-col sm:flex-row gap-4">
                            <button onclick="openOrderModal()" class="px-8 py-3.5 bg-gradient-to-r from-blue-600 to-blue-800 text-white font-semibold rounded-xl shadow-lg shadow-blue-200 hover:shadow-xl hover:scale-105 transition-all flex items-center justify-center gap-2">
                                <i class="fas fa-shopping-cart"></i>Order Now
                            </button>
                            <a href="#contact" class="px-8 py-3.5 border-2 border-slate-300 font-semibold rounded-xl hover:bg-slate-50 hover:border-blue-300 transition flex items-center justify-center gap-2">
                                <i class="fas fa-comment-dots"></i>Request Consultation
                            </a>
                        </div>
                        
                        <div class="grid grid-cols-2 md:grid-cols-4 gap-6 pt-8">
                            <div class="text-center">
                                <div class="text-3xl font-bold text-blue-700">25+</div>
                                <div class="text-sm text-slate-500">Years Experience</div>
                            </div>
                            <div class="text-center">
                                <div class="text-3xl font-bold text-blue-700">500+</div>
                                <div class="text-sm text-slate-500">Projects Completed</div>
                            </div>
                            <div class="text-center">
                                <div class="text-3xl font-bold text-blue-700">40+</div>
                                <div class="text-sm text-slate-500">Countries Served</div>
                            </div>
                            <div class="text-center">
                                <div class="text-3xl font-bold text-blue-700">ISO</div>
                                <div class="text-sm text-slate-500">9001:2015 Certified</div>
                            </div>
                        </div>
                    </div>
                    
                    <div class="flex-1 w-full">
                        <div class="relative">
                            <div class="model-viewer-container">
                                <model-viewer 
                                    id="hero-model-viewer"
                                    src="https://modelviewer.dev/shared-assets/models/Astronaut.glb" 
                                    alt="Industrial Flange 3D Model"
                                    auto-rotate
                                    camera-controls
                                    shadow-intensity="1"
                                    ar
                                    ar-modes="scene-viewer quick-look"
                                    style="width:100%; height:100%;"
                                >
                                    <button slot="ar-button" class="ar-button">
                                        <i class="fas fa-vr-cardboard mr-2"></i>View in AR
                                    </button>
                                    <div class="model-controls">
                                        <button onclick="resetModelView('hero')" class="model-control-btn">
                                            <i class="fas fa-redo"></i> Reset
                                        </button>
                                        <button onclick="toggleAutoRotate('hero')" class="model-control-btn">
                                            <i class="fas fa-play"></i> Auto Rotate
                                        </button>
                                        <button onclick="downloadHeroModel()" class="model-control-btn">
                                            <i class="fas fa-download"></i> CAD
                                        </button>
                                    </div>
                                </model-viewer>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Product Exploration Section -->
        <section id="catalog-access" class="bg-white border-y border-slate-200 py-16 overflow-hidden reveal">
            <div class="max-w-7xl mx-auto px-4">
                <div class="flex flex-col items-center gap-10">
                    <div class="text-center max-w-3xl mx-auto">
                        <span class="text-blue-600 font-bold uppercase tracking-widest text-sm">3D Product Catalog</span>
                        <h2 class="text-4xl font-bold text-slate-900 mt-2 mb-4">Interactive 3D Models</h2>
                        <p class="text-slate-600 text-lg">Explore our products in 3D - rotate, zoom, and examine every detail</p>
                    </div>
                    
                    <!-- 3D Model Thumbnails Grid -->
                    <div class="w-full grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6 mb-12 reveal stagger-delay-1">
                        <!-- Weld Neck Flange -->
                        <div class="model-thumbnail" onclick="updateProduct('wnf')">
                            <div class="model-placeholder">
                                <i class="fas fa-fire"></i>
                                <span class="font-semibold mt-2">Weld Neck Flange</span>
                            </div>
                        </div>
                        
                        <!-- Long Weld Neck -->
                        <div class="model-thumbnail" onclick="updateProduct('lwn')">
                            <div class="model-placeholder">
                                <i class="fas fa-ruler-vertical"></i>
                                <span class="font-semibold mt-2">Long Weld Neck</span>
                            </div>
                        </div>
                        
                        <!-- Slip-On Flange -->
                        <div class="model-thumbnail" onclick="updateProduct('slipon')">
                            <div class="model-placeholder">
                                <i class="fas fa-sliders-h"></i>
                                <span class="font-semibold mt-2">Slip-On Flange</span>
                            </div>
                        </div>
                        
                        <!-- Blind Flange -->
                        <div class="model-thumbnail" onclick="updateProduct('blind')">
                            <div class="model-placeholder">
                                <i class="fas fa-ban"></i>
                                <span class="font-semibold mt-2">Blind Flange</span>
                            </div>
                        </div>
                        
                        <!-- Puddle Flange -->
                        <div class="model-thumbnail" onclick="updateProduct('puddle')">
                            <div class="model-placeholder">
                                <i class="fas fa-water"></i>
                                <span class="font-semibold mt-2">Puddle Flange</span>
                            </div>
                        </div>
                        
                        <!-- Plasma CNC -->
                        <div class="model-thumbnail" onclick="updateProduct('plasma')">
                            <div class="model-placeholder">
                                <i class="fas fa-bolt"></i>
                                <span class="font-semibold mt-2">Plasma CNC</span>
                            </div>
                        </div>
                        
                        <!-- Profile Cutting -->
                        <div class="model-thumbnail" onclick="updateProduct('profile')">
                            <div class="model-placeholder">
                                <i class="fas fa-cut"></i>
                                <span class="font-semibold mt-2">Profile Cutting</span>
                            </div>
                        </div>
                        
                        <!-- All Products -->
                        <div class="model-thumbnail bg-gradient-to-br from-blue-600 to-blue-800" onclick="showAllModels()">
                            <div class="model-placeholder text-white">
                                <i class="fas fa-cube"></i>
                                <span class="font-semibold mt-2">View All Models</span>
                            </div>
                        </div>
                    </div>
                    
                    <div class="w-full flex flex-col lg:flex-row items-center justify-center gap-6">
                        <div class="search-container relative w-full lg:w-96 flex-shrink-0 border-2 border-slate-300 rounded-full bg-white px-6 py-3.5 transition-all">
                            <div class="flex items-center gap-3">
                                <i class="fas fa-search text-slate-400"></i>
                                <input type="text" id="product-search" placeholder="Search product codes, names, or specs..." 
                                       class="bg-transparent border-none outline-none text-base w-full text-slate-700 placeholder:text-slate-400"
                                       onkeyup="handleSearch(this.value)">
                            </div>
                        </div>

                        <div class="w-full overflow-x-auto no-scrollbar py-2">
                            <div class="flex justify-start lg:justify-center gap-3 min-w-max px-2" id="suggestion-bar">
                                <div onclick="updateProduct('wnf')" id="chip-wnf" class="flange-chip active px-5 py-2.5 rounded-full border-2 border-slate-200 bg-white text-sm font-semibold flex items-center gap-2">
                                    <i class="fas fa-fire"></i>Weld Neck
                                </div>
                                <div onclick="updateProduct('lwn')" id="chip-lwn" class="flange-chip px-5 py-2.5 rounded-full border-2 border-slate-200 bg-white text-sm font-semibold flex items-center gap-2">
                                    <i class="fas fa-ruler-vertical"></i>Long Weld Neck
                                </div>
                                <div onclick="updateProduct('slipon')" id="chip-slipon" class="flange-chip px-5 py-2.5 rounded-full border-2 border-slate-200 bg-white text-sm font-semibold flex items-center gap-2">
                                    <i class="fas fa-sliders-h"></i>Slip-On
                                </div>
                                <div onclick="updateProduct('blind')" id="chip-blind" class="flange-chip px-5 py-2.5 rounded-full border-2 border-slate-200 bg-white text-sm font-semibold flex items-center gap-2">
                                    <i class="fas fa-ban"></i>Blind
                                </div>
                                <div onclick="updateProduct('puddle')" id="chip-puddle" class="flange-chip px-5 py-2.5 rounded-full border-2 border-slate-200 bg-white text-sm font-semibold flex items-center gap-2">
                                    <i class="fas fa-water"></i>Puddle
                                </div>
                                <div onclick="updateProduct('plasma')" id="chip-plasma" class="flange-chip px-5 py-2.5 rounded-full border-2 border-slate-200 bg-white text-sm font-semibold flex items-center gap-2">
                                    <i class="fas fa-bolt"></i>Plasma CNC
                                </div>
                                <div onclick="updateProduct('profile')" id="chip-profile" class="flange-chip px-5 py-2.5 rounded-full border-2 border-slate-200 bg-white text-sm font-semibold flex items-center gap-2">
                                    <i class="fas fa-cut"></i>Profile Cutting
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Product Details Section with 3D Viewer -->
        <section id="products" class="py-20 bg-slate-50 reveal">
            <div class="max-w-7xl mx-auto px-4">
                <div class="bg-white p-8 md:p-12 rounded-3xl border border-slate-100 transition-all duration-500 shadow-lg" id="product-card">
                    <div class="prose prose-slate max-w-none">
                        <!-- 3D Model Viewer Section -->
                        <div class="mb-12 reveal stagger-delay-1">
                            <div class="flex flex-col lg:flex-row gap-8 items-start">
                                <!-- 3D Model Viewer -->
                                <div class="flex-1">
                                    <div class="model-viewer-container" id="product-model-container">
                                        <model-viewer 
                                            id="product-model-viewer"
                                            src="https://modelviewer.dev/shared-assets/models/Astronaut.glb" 
                                            alt="3D Product Model"
                                            auto-rotate
                                            camera-controls
                                            shadow-intensity="1"
                                            ar
                                            ar-modes="scene-viewer quick-look"
                                            style="width:100%; height:100%;"
                                        >
                                            <button slot="ar-button" class="ar-button">
                                                <i class="fas fa-vr-cardboard mr-2"></i>View in AR
                                            </button>
                                            <div class="rotation-control">
                                                <label for="rotation-speed">Rotation Speed</label>
                                                <input type="range" id="rotation-speed" min="0" max="5" value="1" step="0.5">
                                                <label for="zoom-level" class="mt-4">Zoom Level</label>
                                                <input type="range" id="zoom-level" min="1" max="10" value="5">
                                            </div>
                                            <div class="model-controls">
                                                <button onclick="resetModelView('product')" class="model-control-btn">
                                                    <i class="fas fa-redo"></i> Reset View
                                                </button>
                                                <button onclick="toggleAutoRotate('product')" class="model-control-btn">
                                                    <i class="fas fa-play"></i> Auto Rotate
                                                </button>
                                                <button onclick="downloadCurrentModel()" class="model-control-btn">
                                                    <i class="fas fa-download"></i> Download CAD
                                                </button>
                                                <button onclick="takeScreenshot()" class="model-control-btn">
                                                    <i class="fas fa-camera"></i> Screenshot
                                                </button>
                                            </div>
                                        </model-viewer>
                                    </div>
                                </div>
                                
                                <!-- Model Info & Controls -->
                                <div class="flex-1">
                                    <div class="bg-gradient-to-br from-slate-900 to-blue-900 rounded-2xl p-6 text-white h-full">
                                        <h4 class="text-xl font-bold mb-4 flex items-center gap-2">
                                            <i class="fas fa-info-circle text-blue-300"></i>3D Model Information
                                        </h4>
                                        <div class="space-y-4 mb-6">
                                            <div>
                                                <div class="text-sm text-blue-300 mb-1">Current Model</div>
                                                <div class="font-bold text-lg" id="current-model-name">Weld Neck Flange</div>
                                            </div>
                                            <div>
                                                <div class="text-sm text-blue-300 mb-1">Format</div>
                                                <div class="font-medium">GLB (GL Transmission Format)</div>
                                            </div>
                                            <div>
                                                <div class="text-sm text-blue-300 mb-1">File Size</div>
                                                <div class="font-medium" id="model-size">~2.5 MB</div>
                                            </div>
                                            <div>
                                                <div class="text-sm text-blue-300 mb-1">Polygons</div>
                                                <div class="font-medium" id="model-polygons">15,428</div>
                                            </div>
                                        </div>
                                        
                                        <div class="space-y-3">
                                            <h5 class="font-bold text-lg mb-2">Controls Guide</h5>
                                            <div class="text-sm text-slate-300 space-y-2">
                                                <div class="flex items-center gap-2">
                                                    <i class="fas fa-mouse-pointer text-blue-300"></i>
                                                    <span>Click & Drag: Rotate model</span>
                                                </div>
                                                <div class="flex items-center gap-2">
                                                    <i class="fas fa-mouse text-blue-300"></i>
                                                    <span>Scroll: Zoom in/out</span>
                                                </div>
                                                <div class="flex items-center gap-2">
                                                    <i class="fas fa-arrows-alt text-blue-300"></i>
                                                    <span>Right-click + Drag: Pan view</span>
                                                </div>
                                                <div class="flex items-center gap-2">
                                                    <i class="fas fa-mobile-alt text-blue-300"></i>
                                                    <span>Touch devices: Use gestures</span>
                                                </div>
                                            </div>
                                        </div>
                                        
                                        <div class="mt-6 pt-6 border-t border-slate-700">
                                            <button onclick="showMeasurementTools()" class="w-full py-3 bg-blue-600 text-white font-bold rounded-xl hover:bg-blue-700 transition mb-3">
                                                <i class="fas fa-ruler-combined mr-2"></i>Measurement Tools
                                            </button>
                                            <button onclick="showCrossSection()" class="w-full py-3 bg-slate-800 text-white font-bold rounded-xl hover:bg-slate-700 transition">
                                                <i class="fas fa-cut mr-2"></i>Cross Section View
                                            </button>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                        
                        <div class="flex flex-col md:flex-row md:items-center justify-between gap-6 mb-10">
                            <div>
                                <h3 class="text-4xl font-bold text-slate-900" id="p-title">Weld Neck Flange (WNF)</h3>
                                <div class="flex items-center gap-4 mt-2">
                                    <span class="px-3 py-1 bg-blue-50 text-blue-700 rounded-full text-xs font-bold">ASME B16.5</span>
                                    <span class="px-3 py-1 bg-green-50 text-green-700 rounded-full text-xs font-bold">ISO Certified</span>
                                    <span class="px-3 py-1 bg-purple-50 text-purple-700 rounded-full text-xs font-bold">3D Model Available</span>
                                </div>
                            </div>
                            <div class="flex gap-3">
                                <button onclick="openOrderModal()" class="px-6 py-3 bg-gradient-to-r from-blue-600 to-blue-800 text-white rounded-lg font-bold shadow-md hover:from-blue-700 hover:to-blue-900 transition flex items-center gap-2">
                                    <i class="fas fa-shopping-cart"></i>Order Now
                                </button>
                                <button onclick="downloadCurrentModel()" class="px-6 py-3 bg-slate-100 text-slate-700 rounded-lg font-bold hover:bg-slate-200 transition flex items-center gap-2">
                                    <i class="fas fa-download"></i>Download 3D Model
                                </button>
                            </div>
                        </div>
                        <p class="text-slate-600 text-xl leading-relaxed mb-10 max-w-4xl" id="p-desc">
                            The Weld Neck Flange is distinguished from other types by its long tapered hub and gentle transition to the thickness of the pipe. Engineered for high-pressure and high-temperature applications where reliability is critical.
                        </p>
                        
                        <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-6 mb-12" id="p-features">
                            <!-- Features populated by JS -->
                        </div>
                        
                        <!-- Additional Product Info -->
                        <div class="bg-blue-50 rounded-2xl p-6 mb-8">
                            <h4 class="text-xl font-bold text-slate-900 mb-4 flex items-center gap-2">
                                <i class="fas fa-cube text-blue-600"></i>3D Model Features
                            </h4>
                            <div class="grid md:grid-cols-2 gap-6">
                                <div>
                                    <h5 class="font-bold text-slate-800 mb-2">Interactive Features</h5>
                                    <ul class="text-slate-600 space-y-1">
                                        <li class="flex items-start gap-2"><i class="fas fa-check text-green-500 mt-1"></i>360° rotation and zoom</li>
                                        <li class="flex items-start gap-2"><i class="fas fa-check text-green-500 mt-1"></i>Augmented Reality (AR) view</li>
                                        <li class="flex items-start gap-2"><i class="fas fa-check text-green-500 mt-1"></i>Cross-section visualization</li>
                                        <li class="flex items-start gap-2"><i class="fas fa-check text-green-500 mt-1"></i>Measurement tools</li>
                                    </ul>
                                </div>
                                <div>
                                    <h5 class="font-bold text-slate-800 mb-2">File Formats Available</h5>
                                    <ul class="text-slate-600 space-y-1">
                                        <li class="flex items-start gap-2"><i class="fas fa-check text-green-500 mt-1"></i>GLB (Web/AR ready)</li>
                                        <li class="flex items-start gap-2"><i class="fas fa-check text-green-500 mt-1"></i>STEP (CAD integration)</li>
                                        <li class="flex items-start gap-2"><i class="fas fa-check text-green-500 mt-1"></i>IGES (Engineering design)</li>
                                        <li class="flex items-start gap-2"><i class="fas fa-check text-green-500 mt-1"></i>STL (3D printing)</li>
                                    </ul>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Detailed Technical Specifications -->
        <section id="specifications" class="py-20 bg-slate-900 text-white reveal">
            <div class="max-w-7xl mx-auto px-4">
                <div class="text-center mb-14">
                    <h2 class="text-4xl md:text-5xl font-bold mb-4" id="spec-title">Technical Specifications</h2>
                    <p class="text-slate-400 max-w-3xl mx-auto text-lg">Comprehensive technical data and material specifications compliant with international standards including ASME, ANSI, EN, and DIN.</p>
                </div>
                
                <div class="grid lg:grid-cols-2 gap-8 mb-12" id="spec-tables-container">
                    <!-- Tables dynamically injected here -->
                </div>
                
                <!-- Standards Compliance -->
                <div class="bg-slate-800/50 rounded-3xl p-8">
                    <h3 class="text-2xl font-bold mb-6 flex items-center gap-3">
                        <i class="fas fa-certificate text-blue-400"></i>Standards & Compliance
                    </h3>
                    <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-6">
                        <div class="bg-slate-900/50 p-5 rounded-2xl">
                            <div class="text-blue-400 text-2xl mb-2">
                                <i class="fas fa-balance-scale"></i>
                            </div>
                            <h4 class="font-bold text-lg mb-2">ASME Standards</h4>
                            <p class="text-slate-400 text-sm">B16.5, B16.47, B31.3, Section VIII Div. 1</p>
                        </div>
                        <div class="bg-slate-900/50 p-5 rounded-2xl">
                            <div class="text-blue-400 text-2xl mb-2">
                                <i class="fas fa-globe-europe"></i>
                            </div>
                            <h4 class="font-bold text-lg mb-2">European Standards</h4>
                            <p class="text-slate-400 text-sm">EN 1092-1, PED 2014/68/EU, ATEX</p>
                        </div>
                        <div class="bg-slate-900/50 p-5 rounded-2xl">
                            <div class="text-blue-400 text-2xl mb-2">
                                <i class="fas fa-industry"></i>
                            </div>
                            <h4 class="font-bold text-lg mb-2">Material Standards</h4>
                            <p class="text-slate-400 text-sm">ASTM A105, A182, A350, A694</p>
                        </div>
                        <div class="bg-slate-900/50 p-5 rounded-2xl">
                            <div class="text-blue-400 text-2xl mb-2">
                                <i class="fas fa-shield-alt"></i>
                            </div>
                            <h4 class="font-bold text-lg mb-2">Quality Certifications</h4>
                            <p class="text-slate-400 text-sm">ISO 9001:2015, PED, NORSOK, API</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- 3D Gallery Section -->
        <section id="3d-gallery" class="py-24 bg-white reveal">
            <div class="max-w-7xl mx-auto px-4">
                <div class="text-center mb-16">
                    <span class="text-blue-600 font-bold uppercase tracking-widest text-sm">3D Product Gallery</span>
                    <h2 class="text-4xl md:text-5xl font-bold text-slate-900 mt-2 mb-4">Explore All Products in 3D</h2>
                    <p class="text-slate-600 max-w-3xl mx-auto text-lg">Click on any product to view its interactive 3D model with full technical details</p>
                </div>
                
                <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
                    <!-- Weld Neck Flange -->
                    <div class="bg-slate-50 rounded-3xl overflow-hidden border border-slate-200 hover:border-blue-300 transition-all duration-300">
                        <div class="model-viewer-container" style="height: 250px;">
                            <model-viewer 
                                src="https://modelviewer.dev/shared-assets/models/Astronaut.glb"
                                alt="Weld Neck Flange 3D"
                                camera-controls
                                auto-rotate
                                style="width:100%; height:100%;"
                            >
                            </model-viewer>
                        </div>
                        <div class="p-6">
                            <h4 class="font-bold text-xl text-slate-900 mb-2">Weld Neck Flange</h4>
                            <p class="text-slate-600 mb-4">High-pressure applications with tapered hub design</p>
                            <div class="flex gap-3">
                                <button onclick="updateProduct('wnf')" class="flex-1 py-2.5 bg-blue-600 text-white rounded-lg font-medium hover:bg-blue-700 transition text-sm">
                                    <i class="fas fa-expand-alt mr-2"></i>View 3D
                                </button>
                                <button onclick="openOrderModalWithProduct('wnf')" class="flex-1 py-2.5 bg-slate-200 text-slate-700 rounded-lg font-medium hover:bg-slate-300 transition text-sm">
                                    <i class="fas fa-shopping-cart mr-2"></i>Order
                                </button>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Long Weld Neck -->
                    <div class="bg-slate-50 rounded-3xl overflow-hidden border border-slate-200 hover:border-blue-300 transition-all duration-300">
                        <div class="model-viewer-container" style="height: 250px;">
                            <model-viewer 
                                src="https://modelviewer.dev/shared-assets/models/NeilArmstrong.glb"
                                alt="Long Weld Neck 3D"
                                camera-controls
                                auto-rotate
                                style="width:100%; height:100%;"
                            >
                            </model-viewer>
                        </div>
                        <div class="p-6">
                            <h4 class="font-bold text-xl text-slate-900 mb-2">Long Weld Neck</h4>
                            <p class="text-slate-600 mb-4">Pressure vessel nozzles with extended hub</p>
                            <div class="flex gap-3">
                                <button onclick="updateProduct('lwn')" class="flex-1 py-2.5 bg-blue-600 text-white rounded-lg font-medium hover:bg-blue-700 transition text-sm">
                                    <i class="fas fa-expand-alt mr-2"></i>View 3D
                                </button>
                                <button onclick="openOrderModalWithProduct('lwn')" class="flex-1 py-2.5 bg-slate-200 text-slate-700 rounded-lg font-medium hover:bg-slate-300 transition text-sm">
                                    <i class="fas fa-shopping-cart mr-2"></i>Order
                                </button>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Slip-On Flange -->
                    <div class="bg-slate-50 rounded-3xl overflow-hidden border border-slate-200 hover:border-blue-300 transition-all duration-300">
                        <div class="model-viewer-container" style="height: 250px;">
                            <model-viewer 
                                src="https://modelviewer.dev/shared-assets/models/RobotExpressive.glb"
                                alt="Slip-On Flange 3D"
                                camera-controls
                                auto-rotate
                                style="width:100%; height:100%;"
                            >
                            </model-viewer>
                        </div>
                        <div class="p-6">
                            <h4 class="font-bold text-xl text-slate-900 mb-2">Slip-On Flange</h4>
                            <p class="text-slate-600 mb-4">Cost-effective solution for standard pressure duty</p>
                            <div class="flex gap-3">
                                <button onclick="updateProduct('slipon')" class="flex-1 py-2.5 bg-blue-600 text-white rounded-lg font-medium hover:bg-blue-700 transition text-sm">
                                    <i class="fas fa-expand-alt mr-2"></i>View 3D
                                </button>
                                <button onclick="openOrderModalWithProduct('slipon')" class="flex-1 py-2.5 bg-slate-200 text-slate-700 rounded-lg font-medium hover:bg-slate-300 transition text-sm">
                                    <i class="fas fa-shopping-cart mr-2"></i>Order
                                </button>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Blind Flange -->
                    <div class="bg-slate-50 rounded-3xl overflow-hidden border border-slate-200 hover:border-blue-300 transition-all duration-300">
                        <div class="model-viewer-container" style="height: 250px;">
                            <model-viewer 
                                src="https://modelviewer.dev/shared-assets/models/NeilArmstrong.glb"
                                alt="Blind Flange 3D"
                                camera-controls
                                auto-rotate
                                style="width:100%; height:100%;"
                            >
                            </model-viewer>
                        </div>
                        <div class="p-6">
                            <h4 class="font-bold text-xl text-slate-900 mb-2">Blind Flange</h4>
                            <p class="text-slate-600 mb-4">System closure and pressure isolation</p>
                            <div class="flex gap-3">
                                <button onclick="updateProduct('blind')" class="flex-1 py-2.5 bg-blue-600 text-white rounded-lg font-medium hover:bg-blue-700 transition text-sm">
                                    <i class="fas fa-expand-alt mr-2"></i>View 3D
                                </button>
                                <button onclick="openOrderModalWithProduct('blind')" class="flex-1 py-2.5 bg-slate-200 text-slate-700 rounded-lg font-medium hover:bg-slate-300 transition text-sm">
                                    <i class="fas fa-shopping-cart mr-2"></i>Order
                                </button>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Puddle Flange -->
                    <div class="bg-slate-50 rounded-3xl overflow-hidden border border-slate-200 hover:border-blue-300 transition-all duration-300">
                        <div class="model-viewer-container" style="height: 250px;">
                            <model-viewer 
                                src="https://modelviewer.dev/shared-assets/models/Astronaut.glb"
                                alt="Puddle Flange 3D"
                                camera-controls
                                auto-rotate
                                style="width:100%; height:100%;"
                            >
                            </model-viewer>
                        </div>
                        <div class="p-6">
                            <h4 class="font-bold text-xl text-slate-900 mb-2">Puddle Flange</h4>
                            <p class="text-slate-600 mb-4">Waterproofing for pipe penetrations</p>
                            <div class="flex gap-3">
                                <button onclick="updateProduct('puddle')" class="flex-1 py-2.5 bg-blue-600 text-white rounded-lg font-medium hover:bg-blue-700 transition text-sm">
                                    <i class="fas fa-expand-alt mr-2"></i>View 3D
                                </button>
                                <button onclick="openOrderModalWithProduct('puddle')" class="flex-1 py-2.5 bg-slate-200 text-slate-700 rounded-lg font-medium hover:bg-slate-300 transition text-sm">
                                    <i class="fas fa-shopping-cart mr-2"></i>Order
                                </button>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Plasma CNC -->
                    <div class="bg-slate-50 rounded-3xl overflow-hidden border border-slate-200 hover:border-blue-300 transition-all duration-300">
                        <div class="model-viewer-container" style="height: 250px;">
                            <model-viewer 
                                src="https://modelviewer.dev/shared-assets/models/RobotExpressive.glb"
                                alt="Plasma CNC 3D"
                                camera-controls
                                auto-rotate
                                style="width:100%; height:100%;"
                            >
                            </model-viewer>
                        </div>
                        <div class="p-6">
                            <h4 class="font-bold text-xl text-slate-900 mb-2">Plasma CNC Cutting</h4>
                            <p class="text-slate-600 mb-4">High-precision automated cutting service</p>
                            <div class="flex gap-3">
                                <button onclick="updateProduct('plasma')" class="flex-1 py-2.5 bg-blue-600 text-white rounded-lg font-medium hover:bg-blue-700 transition text-sm">
                                    <i class="fas fa-expand-alt mr-2"></i>View 3D
                                </button>
                                <button onclick="openOrderModalWithProduct('plasma')" class="flex-1 py-2.5 bg-slate-200 text-slate-700 rounded-lg font-medium hover:bg-slate-300 transition text-sm">
                                    <i class="fas fa-shopping-cart mr-2"></i>Order
                                </button>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="text-center mt-16">
                    <button onclick="showAllModels()" class="px-8 py-3.5 bg-gradient-to-r from-blue-600 to-blue-800 text-white font-bold rounded-xl hover:from-blue-700 hover:to-blue-900 transition shadow-lg">
                        <i class="fas fa-cube mr-2"></i>View All 3D Models Gallery
                    </button>
                </div>
            </div>
        </section>

        <!-- "Know More" Deep Dive Section -->
        <section id="about" class="py-24 bg-white reveal">
            <div class="max-w-7xl mx-auto px-4">
                <div class="grid lg:grid-cols-2 gap-16 items-start">
                    <div class="space-y-10">
                        <div>
                            <span class="text-blue-600 font-bold uppercase tracking-widest text-sm">Industrial Insight</span>
                            <h2 class="text-5xl font-bold text-slate-900 mt-2">Engineering Excellence in Flange Manufacturing</h2>
                            <p class="text-slate-600 mt-6 leading-relaxed text-lg">
                                At <strong class="text-blue-700">Ultimate Flange</strong>, we believe that a flange is more than just a connector; it is a critical safety component of your infrastructure. Our engineering philosophy centers on four core pillars that ensure reliability under the most demanding conditions.
                            </p>
                        </div>

                        <div class="space-y-6">
                            <div class="knowledge-card p-8 rounded-3xl">
                                <div class="flex items-start gap-4">
                                    <div class="w-12 h-12 bg-blue-100 rounded-xl flex items-center justify-center flex-shrink-0">
                                        <i class="fas fa-atom text-blue-600 text-xl"></i>
                                    </div>
                                    <div>
                                        <h4 class="font-bold text-slate-900 text-xl mb-3">Metallurgical Integrity</h4>
                                        <p class="text-slate-600 leading-relaxed">
                                            Every component starts with raw forging stock that undergoes rigorous ultrasonic testing. We ensure zero internal voids or inclusions that could lead to failure under high-cycle fatigue or cryogenic temperatures. Our material traceability is certified to EN 10204 3.1 standards.
                                        </p>
                                    </div>
                                </div>
                            </div>

                            <div class="knowledge-card p-8 rounded-3xl">
                                <div class="flex items-start gap-4">
                                    <div class="w-12 h-12 bg-blue-100 rounded-xl flex items-center justify-center flex-shrink-0">
                                        <i class="fas fa-ruler-combined text-blue-600 text-xl"></i>
                                    </div>
                                    <div>
                                        <h4 class="font-bold text-slate-900 text-xl mb-3">Precision Geometry</h4>
                                        <p class="text-slate-600 leading-relaxed">
                                            Using CNC vertical turning centers with laser measurement systems, we maintain tolerances of ±0.05mm. Our gasket faces are machined to exact Ra values (0.8-3.2 μm) to guarantee 100% leak-proof sealing upon installation, even in high-vibration environments.
                                        </p>
                                    </div>
                                </div>
                            </div>

                            <div class="knowledge-card p-8 rounded-3xl">
                                <div class="flex items-start gap-4">
                                    <div class="w-12 h-12 bg-blue-100 rounded-xl flex items-center justify-center flex-shrink-0">
                                        <i class="fas fa-bolt text-blue-600 text-xl"></i>
                                    </div>
                                    <div>
                                        <h4 class="font-bold text-slate-900 text-xl mb-3">Advanced Fabrication</h4>
                                        <p class="text-slate-600 leading-relaxed">
                                            Beyond standard flanges, our Plasma CNC division provides custom profile cutting from carbon or stainless steel up to 100mm thick with minimal Heat Affected Zones (HAZ). Our oxy-fuel cutting handles sections up to 350mm for structural applications.
                                        </p>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>

                    <div class="lg:sticky lg:top-24 bg-gradient-to-br from-slate-900 to-blue-900 rounded-3xl p-10 text-white shadow-2xl">
                        <h3 class="text-3xl font-bold mb-12">Why Partner With Us?</h3>
                        <div class="space-y-10">
                            <div class="flex gap-6">
                                <div class="text-blue-300 font-bold text-4xl">01</div>
                                <div>
                                    <h5 class="font-bold text-xl mb-3">Full Traceability & Certification</h5>
                                    <p class="text-slate-300 leading-relaxed">Comprehensive EN 10204 3.1 certification provided with every single order, ensuring 100% material transparency, compliance, and audit readiness for critical projects.</p>
                                </div>
                            </div>
                            <div class="flex gap-6">
                                <div class="text-blue-300 font-bold text-4xl">02</div>
                                <div>
                                    <h5 class="font-bold text-xl mb-3">Rapid Engineering Support</h5>
                                    <p class="text-slate-300 leading-relaxed">Our in-house design team can translate complex technical requirements into CNC-ready CAD files in under 4 hours. We provide FEA analysis for custom applications.</p>
                                </div>
                            </div>
                            <div class="flex gap-6">
                                <div class="text-blue-300 font-bold text-4xl">03</div>
                                <div>
                                    <h5 class="font-bold text-xl mb-3">Global Logistics Network</h5>
                                    <p class="text-slate-300 leading-relaxed">Priority logistics partnerships with DHL, FedEx Industrial, and specialized heavy freight carriers ensure your critical components reach offshore platforms or remote sites on schedule.</p>
                                </div>
                            </div>
                            <div class="flex gap-6">
                                <div class="text-blue-300 font-bold text-4xl">04</div>
                                <div>
                                    <h5 class="font-bold text-xl mb-3">Technical Consultation</h5>
                                    <p class="text-slate-300 leading-relaxed">Our engineers are available for on-site consultation, failure analysis, and material selection guidance to optimize your piping systems for performance and longevity.</p>
                                </div>
                            </div>
                        </div>
                        
                        <div class="mt-12 pt-8 border-t border-slate-700">
                            <button onclick="openOrderModal()" class="w-full py-4 bg-white text-slate-900 font-bold rounded-xl hover:bg-blue-50 transition text-center block">
                                <i class="fas fa-calendar-check mr-2"></i>Request Quotation
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Contact Section -->
        <section id="contact" class="py-20 bg-slate-50 reveal">
            <div class="max-w-7xl mx-auto px-4">
                <div class="text-center mb-16">
                    <h2 class="text-4xl md:text-5xl font-bold text-slate-900 mb-4">Get in Touch</h2>
                    <p class="text-slate-600 max-w-3xl mx-auto text-lg">Contact our engineering team for technical support, quotes, or consultation on your next project.</p>
                </div>
                
                <div class="grid lg:grid-cols-3 gap-8">
                    <div class="bg-white p-8 rounded-3xl shadow-lg">
                        <div class="w-14 h-14 bg-blue-100 rounded-2xl flex items-center justify-center mb-6">
                            <i class="fas fa-phone-alt text-blue-600 text-2xl"></i>
                        </div>
                        <h3 class="text-xl font-bold text-slate-900 mb-3">Call Us</h3>
                        <p class="text-slate-600 mb-4">Speak directly with our technical sales team</p>
                        <a href="tel:+1234567890" class="text-blue-700 font-bold text-lg hover:text-blue-800">+91 7307709671</a>
                        <p class="text-slate-500 text-sm mt-2">Mon-Fri, 8:00 AM - 6:00 PM EST</p>
                    </div>
                    
                    <div class="bg-white p-8 rounded-3xl shadow-lg">
                        <div class="w-14 h-14 bg-blue-100 rounded-2xl flex items-center justify-center mb-6">
                            <i class="fas fa-envelope text-blue-600 text-2xl"></i>
                        </div>
                        <h3 class="text-xl font-bold text-slate-900 mb-3">Email Us</h3>
                        <p class="text-slate-600 mb-4">Send detailed project requirements for quotes</p>
                        <a href="mailto:sales@ultimateflange.com" class="text-blue-700 font-bold text-lg hover:text-blue-800">sales@ultimateflange.com</a>
                        <p class="text-slate-500 text-sm mt-2">Response within 4 business hours</p>
                    </div>
                    
                    <div class="bg-white p-8 rounded-3xl shadow-lg">
                        <div class="w-14 h-14 bg-blue-100 rounded-2xl flex items-center justify-center mb-6">
                            <i class="fas fa-map-marker-alt text-blue-600 text-2xl"></i>
                        </div>
                        <h3 class="text-xl font-bold text-slate-900 mb-3">Visit Us</h3>
                        <p class="text-slate-600 mb-4">Schedule a plant tour or in-person meeting</p>
                        <address class="text-slate-700 not-italic font-medium">
                            pipe road kurla west<br>
                            mumbai, pin-400070<br>
                            india maharastra
                        </address>
                        <p class="text-slate-500 text-sm mt-2">By appointment only</p>
                    </div>
                </div>
                
                <!-- Quick Order Button -->
                <div class="mt-16 text-center">
                    <button onclick="openOrderModal()" class="px-10 py-4 bg-gradient-to-r from-green-600 to-green-800 text-white font-bold rounded-xl hover:from-green-700 hover:to-green-900 transition shadow-lg text-lg">
                        <i class="fas fa-bolt mr-2"></i>Quick Order Request
                    </button>
                    <p class="text-slate-500 mt-4 text-sm">Get pricing and delivery information in 24 hours</p>
                </div>
            </div>
        </section>

        <!-- Footer -->
        <footer class="bg-slate-900 text-white py-16 px-4">
            <div class="max-w-7xl mx-auto">
                <div class="grid md:grid-cols-4 gap-10 mb-12">
                    <div>
                        <div class="flex items-center gap-3 mb-6">
                            <div class="w-10 h-10 bg-blue-600 rounded-xl flex items-center justify-center">
                                <i class="fas fa-cogs text-white"></i>
                            </div>
                            <span class="text-xl font-bold">UltimateFlange</span>
                        </div>
                        <p class="text-slate-400 text-sm leading-relaxed">Setting the global standard for precision industrial components since 1999.</p>
                    </div>
                    
                    <div>
                        <h4 class="font-bold text-lg mb-6">Products</h4>
                        <ul class="space-y-3 text-slate-400">
                            <li><a href="#" class="hover:text-white transition">Weld Neck Flanges</a></li>
                            <li><a href="#" class="hover:text-white transition">Slip-On Flanges</a></li>
                            <li><a href="#" class="hover:text-white transition">Blind Flanges</a></li>
                            <li><a href="#" class="hover:text-white transition">Specialty Flanges</a></li>
                            <li><a href="#" class="hover:text-white transition">Plasma CNC Cutting</a></li>
                        </ul>
                    </div>
                    
                    <div>
                        <h4 class="font-bold text-lg mb-6">Resources</h4>
                        <ul class="space-y-3 text-slate-400">
                            <li><a href="#" class="hover:text-white transition">Technical Specifications</a></li>
                            <li><a href="#" class="hover:text-white transition">CAD Drawings</a></li>
                            <li><a href="#" class="hover:text-white transition">Material Selection Guide</a></li>
                            <li><a href="#" class="hover:text-white transition">Installation Manuals</a></li>
                            <li><a href="#" class="hover:text-white transition">3D Models</a></li>
                        </ul>
                    </div>
                    
                    <div>
                        <h4 class="font-bold text-lg mb-6">Ordering Process</h4>
                        <ul class="space-y-3 text-slate-400">
                            <li><a href="#" onclick="openOrderModal(); return false;" class="hover:text-white transition">Request Quotation</a></li>
                            <li><a href="#" class="hover:text-white transition">Pricing & Delivery</a></li>
                            <li><a href="#" class="hover:text-white transition">Payment Terms</a></li>
                            <li><a href="#" class="hover:text-white transition">Order Tracking</a></li>
                            <li><a href="#" class="hover:text-white transition">Supplier Portal</a></li>
                        </ul>
                    </div>
                </div>
                
                <div class="pt-8 border-t border-slate-800 flex flex-col md:flex-row justify-between items-center">
                    <p class="text-slate-400 text-sm">© 2024 Ultimate Flange Manufacturing Ltd. All rights reserved.</p>
                    <div class="flex gap-4 mt-4 md:mt-0">
                        <a href="#" class="text-slate-400 hover:text-white">
                            <i class="fab fa-linkedin text-lg"></i>
                        </a>
                        <a href="#" class="text-slate-400 hover:text-white">
                            <i class="fab fa-twitter text-lg"></i>
                        </a>
                        <a href="#" class="text-slate-400 hover:text-white">
                            <i class="fab fa-youtube text-lg"></i>
                        </a>
                    </div>
                </div>
            </div>
        </footer>
    </div>

    <script>
        // Enhanced Authentication Management
        function toggleAuthView(view) {
            document.getElementById('login-form').classList.toggle('hidden', view !== 'login');
            document.getElementById('signup-form').classList.toggle('hidden', view !== 'signup');
        }
        
        function closeAuth() {
            document.getElementById('auth-overlay').classList.add('hidden');
        }

        function handleAuth(event, userType) {
            if (event) event.preventDefault();
            const loader = document.getElementById('transition-loader');
            loader.style.left = '0%';
            
            setTimeout(() => {
                const statusBadge = document.getElementById('user-status');
                const mobileStatus = document.getElementById('mobile-user-status');
                
                if (userType === 'visitor') {
                    statusBadge.innerText = 'Visitor Mode';
                    statusBadge.className = 'px-3 py-1.5 bg-blue-50 rounded-full text-xs font-bold text-blue-600 uppercase border border-blue-100';
                    statusBadge.innerHTML = '<i class="fas fa-user mr-1"></i>Visitor';
                    
                    mobileStatus.innerText = 'Visitor Mode';
                    mobileStatus.className = 'px-3 py-2 bg-blue-50 rounded-lg text-sm font-bold text-blue-600';
                } else {
                    statusBadge.innerText = 'Partner';
                    statusBadge.className = 'px-3 py-1.5 bg-blue-50 rounded-full text-xs font-bold text-blue-600 uppercase border border-blue-100';
                    statusBadge.innerHTML = '<i class="fas fa-user-shield mr-1"></i>Partner';
                    
                    mobileStatus.innerText = 'Partner';
                    mobileStatus.className = 'px-3 py-2 bg-slate-100 rounded-lg text-sm font-bold text-slate-600';
                }

                document.getElementById('auth-overlay').classList.add('hidden');
                document.body.classList.add('authenticated');
                loader.style.left = '100%';
                setTimeout(() => loader.style.left = '-100%', 1200);
                initReveal();
                updateProduct('wnf');
            }, 1000);
        }

        function logout() {
            const loader = document.getElementById('transition-loader');
            loader.style.left = '0%';
            setTimeout(() => {
                document.getElementById('auth-overlay').classList.remove('hidden');
                document.body.classList.remove('authenticated');
                loader.style.left = '100%';
                setTimeout(() => loader.style.left = '-100%', 1200);
                toggleMobileMenu(false);
            }, 800);
        }
        
        // Mobile Menu Toggle
        function toggleMobileMenu(forceClose) {
            const menu = document.getElementById('mobile-menu');
            if (forceClose === false) {
                menu.classList.remove('active');
            } else {
                menu.classList.toggle('active');
            }
        }

        // Order Modal Functions
        let currentOrderStep = 1;

        function openOrderModal() {
            document.getElementById('order-modal').classList.remove('hidden');
            document.body.style.overflow = 'hidden';
            resetOrderSteps();
        }
        
        function openOrderModalWithProduct(productKey) {
            openOrderModal();
            // Set the product in the order modal
            document.getElementById('order-product').value = productKey;
        }
        
        function closeOrderModal() {
            document.getElementById('order-modal').classList.add('hidden');
            document.body.style.overflow = 'auto';
        }

        function resetOrderSteps() {
            currentOrderStep = 1;
            document.getElementById('current-step').textContent = '1';
            
            // Hide all steps
            for (let i = 1; i <= 4; i++) {
                const stepEl = document.getElementById(`order-step-${i}`);
                if (stepEl) stepEl.classList.add('hidden');
            }
            
            // Show step 1
            document.getElementById('order-step-1').classList.remove('hidden');
            
            // Update step indicators
            updateStepIndicators();
        }

        function updateStepIndicators() {
            const indicators = document.querySelectorAll('#order-modal .step-indicator');
            indicators.forEach((indicator, index) => {
                const stepNum = index + 1;
                if (stepNum === currentOrderStep) {
                    indicator.classList.remove('bg-slate-200', 'text-slate-500', 'bg-green-500');
                    indicator.classList.add('bg-blue-600', 'text-white');
                } else if (stepNum < currentOrderStep) {
                    indicator.classList.remove('bg-slate-200', 'text-slate-500', 'bg-blue-600');
                    indicator.classList.add('bg-green-500', 'text-white');
                } else {
                    indicator.classList.remove('bg-blue-600', 'text-white', 'bg-green-500');
                    indicator.classList.add('bg-slate-200', 'text-slate-500');
                }
            });
        }

        function nextOrderStep(step) {
            if (step < 1 || step > 4) return;
            
            // Update review section before moving to step 3
            if (step === 3) {
                updateReviewSection();
            }
            
            // Hide current step
            document.getElementById(`order-step-${currentOrderStep}`).classList.add('hidden');
            
            // Show new step
            currentOrderStep = step;
            document.getElementById(`order-step-${step}`).classList.remove('hidden');
            document.getElementById('current-step').textContent = step.toString();
            
            // Update step indicators
            updateStepIndicators();
        }

        function prevOrderStep(step) {
            nextOrderStep(step);
        }

        function updateReviewSection() {
            // Get values from form
            const productSelect = document.getElementById('order-product');
            const productText = productSelect.options[productSelect.selectedIndex].text;
            const quantity = document.getElementById('order-quantity').value;
            const materialSelect = document.getElementById('order-material');
            const materialText = materialSelect.options[materialSelect.selectedIndex].text;
            const contactMethod = document.querySelector('input[name="contactMethod"]:checked').value;
            
            // Update review section
            document.getElementById('review-product').textContent = productText;
            document.getElementById('review-quantity').textContent = `${quantity} pieces`;
            document.getElementById('review-material').textContent = materialText;
            document.getElementById('review-contact').textContent = contactMethod.charAt(0).toUpperCase() + contactMethod.slice(1);
        }

        function submitOrder() {
            // Get order data
            const orderData = {
                product: document.getElementById('order-product').value,
                productName: document.getElementById('order-product').options[document.getElementById('order-product').selectedIndex].text,
                quantity: document.getElementById('order-quantity').value,
                size: document.getElementById('order-size').value,
                material: document.getElementById('order-material').value,
                materialName: document.getElementById('order-material').options[document.getElementById('order-material').selectedIndex].text,
                specs: document.getElementById('order-specs').value,
                firstName: document.getElementById('order-firstname').value,
                lastName: document.getElementById('order-lastname').value,
                email: document.getElementById('order-email').value,
                phone: document.getElementById('order-phone').value,
                company: document.getElementById('order-company').value,
                address: document.getElementById('order-address').value,
                contactMethod: document.querySelector('input[name="contactMethod"]:checked').value,
                timestamp: new Date().toISOString(),
                orderId: `UF-ORD-${Date.now().toString().slice(-6)}`
            };
            
            // Log order data (in production, this would be sent to backend)
            console.log('Order submitted to supplier:', orderData);
            
            // Update order reference
            document.getElementById('order-reference').textContent = orderData.orderId;
            
            // Show confirmation step
            nextOrderStep(4);
            
            // Simulate sending to supplier (in production, use API/backend)
            simulateSupplierNotification(orderData);
        }

        function simulateSupplierNotification(orderData) {
            console.log('Sending notification to supplier team...');
            console.log('Supplier Email: supplier@ultimateflange.com');
            console.log('Supplier Phone: +1 (234) 567-8910');
            console.log('Order Details:', orderData);
            
            // In production, you would make an API call here
            // fetch('/api/send-to-supplier', {
            //     method: 'POST',
            //     headers: {'Content-Type': 'application/json'},
            //     body: JSON.stringify(orderData)
            // })
            
            setTimeout(() => {
                console.log('Supplier notified successfully!');
                console.log('Supplier will send:');
                console.log('1. Pricing quotation');
                console.log('2. Delivery timeline');
                console.log('3. Proforma invoice');
            }, 1000);
        }

        // Product Data with 3D Models
        const productData = {
            wnf: {
                title: "Weld Neck Flange (WNF)",
                desc: "High-performance flanges engineered for severe service conditions, featuring a long tapered hub that reduces stress concentrations and improves fatigue resistance. Ideal for high-pressure, high-temperature, and cryogenic applications.",
                model3d: "https://modelviewer.dev/shared-assets/models/Astronaut.glb",
                modelSize: "2.3 MB",
                polygons: "18,542",
                features: [
                    "Designed for high-pressure systems (up to 2500#)",
                    "Long tapered hub reduces stress concentration",
                    "Matches pipe internal diameter for smooth flow",
                    "Certified for high-temperature and cryogenic service",
                    "ASME B16.5 compliant design",
                    "Available with RF, RTJ, or FF faces"
                ],
                specs: {
                    general: {
                        "Size Range": "1/2\" to 72\" (DN15 to DN1800)",
                        "Standards": "ANSI B16.5, B16.47, ASME Section VIII",
                        "Pressure Ratings": "150# to 2500# (PN6 to PN420)",
                        "Face Types": "RF, RTJ, FF, LMF",
                        "Bolt Circle": "Per ASME B16.5 tables",
                        "Thickness": "Schedule 10 to XXS"
                    },
                    materials: {
                        "Stainless Steel": "A182 F316/304L, F316H, F321",
                        "Carbon Steel": "A105, A350 LF2, A694 F52",
                        "Alloy Steel": "A182 F11, F22, F91",
                        "Duplex/Super Duplex": "F51 (2205), F53 (2507)",
                        "Nickel Alloys": "Inconel 625, Monel 400, Hastelloy"
                    }
                }
            },
            lwn: {
                title: "Long Weld Neck Flange (LWN)",
                desc: "Commonly used for nozzles on pressure vessels and reactors, LWN flanges provide an extended hub to match nominal pipe size without requiring additional pipe sections or welding preparations.",
                model3d: "https://modelviewer.dev/shared-assets/models/NeilArmstrong.glb",
                modelSize: "2.8 MB",
                polygons: "22,156",
                features: [
                    "Extended hub reduces required welding",
                    "Ideal for pressure vessel connections",
                    "Heavy wall construction for reinforcement",
                    "Standardized neck dimensions per ASME",
                    "Smooth bore transition"
                ],
                specs: {
                    general: {
                        "Size Range": "1/2\" to 24\" (DN15 to DN600)",
                        "Standards": "ASME B16.5, API 605",
                        "Pressure Ratings": "150# to 2500#",
                        "Face Types": "RF, RTJ",
                        "Neck Length": "Per MSS SP-44 or customer spec",
                        "Application": "Pressure Vessel Nozzles"
                    },
                    materials: {
                        "Stainless Steel": "A182 F316/316L, F304H",
                        "Carbon Steel": "A105, A350 LF2, A266 Cl.2",
                        "Alloy Steel": "A182 F9, F11, F22",
                        "Special Alloys": "Inconel 625, Alloy 20"
                    }
                }
            },
            slipon: {
                title: "Slip-On Flange",
                desc: "A cost-effective flange solution that slides over the pipe and is welded both inside and outside for strength. Easier to align than weld neck flanges and suitable for lower pressure applications.",
                model3d: "https://modelviewer.dev/shared-assets/models/RobotExpressive.glb",
                modelSize: "1.9 MB",
                polygons: "15,428",
                features: [
                    "Lower installation cost and time",
                    "Easy alignment during installation",
                    "Suitable for standard pressure duty",
                    "Internal and external welding for strength",
                    "Available in raised face or flat face"
                ],
                specs: {
                    general: {
                        "Size Range": "1/2\" to 60\" (DN15 to DN1500)",
                        "Standards": "ANSI B16.5, B16.47, EN 1092-1",
                        "Pressure Ratings": "150# to 600# (PN6 to PN100)",
                        "Face Types": "RF, FF",
                        "Hub Length": "Shorter than weld neck",
                        "Weight": "Approximately 1/3 less than WNF"
                    },
                    materials: {
                        "Stainless Steel": "A182 F304L, F316L",
                        "Carbon Steel": "A105, A350 LF2",
                        "Alloy Steel": "Limited grades available",
                        "Mild Steel": "S235JR, S355JR"
                    }
                }
            },
            blind: {
                title: "Blind Flange",
                desc: "Used to seal the end of a piping system, pressure vessel, or valve. Designed to handle high stress from internal pressure and provide a positive shut-off for maintenance or future expansion.",
                model3d: "https://modelviewer.dev/shared-assets/models/NeilArmstrong.glb",
                modelSize: "2.1 MB",
                polygons: "16,892",
                features: [
                    "Pressure isolation and system closure",
                    "Removable for maintenance access",
                    "Solid forged construction for strength",
                    "Critical safety shut-off component",
                    "Available with or without jack screw holes"
                ],
                specs: {
                    general: {
                        "Size Range": "1/2\" to 72\" (DN15 to DN1800)",
                        "Standards": "B16.5, B16.47, EN 1092-1",
                        "Pressure Ratings": "150# to 2500#",
                        "Face Types": "RF, RTJ, FF",
                        "Thickness": "Per ASME B16.5 Table 8",
                        "Test Pressure": "1.5x rated pressure"
                    },
                    materials: {
                        "Stainless Steel": "A182 F316L, F304L",
                        "Carbon Steel": "A105, A350 LF2",
                        "Alloy Steel": "A182 F22, F11",
                        "Lining Options": "Rubber, PTFE, Glass"
                    }
                }
            },
            puddle: {
                title: "Puddle Flange",
                desc: "Specialty flange used in construction to prevent fluid seepage where pipes pass through concrete walls or foundations. Provides a watertight seal between pipe and structure.",
                model3d: "https://modelviewer.dev/shared-assets/models/Astronaut.glb",
                modelSize: "2.5 MB",
                polygons: "19,234",
                features: [
                    "Waterproofing for pipe penetrations",
                    "Cast iron or fabricated construction",
                    "Civil engineering standard compliance",
                    "Watertight seal with concrete",
                    "Available with or without anchoring studs"
                ],
                specs: {
                    general: {
                        "Size Range": "DN50 to DN2000",
                        "Standards": "EN1092-1, BS4504, AWWA",
                        "Pressure Ratings": "PN6, PN10, PN16",
                        "Application": "Water Treatment, Sewage",
                        "Seal Type": "Rubber gasket or mechanical"
                    },
                    materials: {
                        "Stainless Steel": "316 / 304, 1.4404 / 1.4301",
                        "Carbon Steel": "Galvanized S235, S355",
                        "Coating": "Fusion Bonded Epoxy, Hot Dip Galv",
                        "Other Materials": "Ductile Iron EN-GJS-400-15"
                    }
                }
            },
            plasma: {
                title: "Plasma CNC Cutting",
                desc: "High-precision automated plasma cutting service for custom plate shapes, flange blanks, and structural components with tight tolerances and superior edge quality.",
                model3d: "https://modelviewer.dev/shared-assets/models/RobotExpressive.glb",
                modelSize: "3.2 MB",
                polygons: "25,678",
                features: [
                    "Cutting capacity up to 100mm thickness",
                    "Complex CAD geometry translation",
                    "Fast turnaround (3-5 business days)",
                    "Superior edge finish with minimal dross",
                    "Nesting optimization for material efficiency"
                ],
                specs: {
                    general: {
                        "Max Plate Size": "3000mm x 6000mm (10' x 20')",
                        "Thickness Range": "3mm to 100mm (1/8\" to 4\")",
                        "Tolerance": "± 1.5mm (± 0.060\")",
                        "Edge Quality": "Ra 25-50 μm, minimal HAZ",
                        "Bevel Cutting": "Up to 45 degrees"
                    },
                    materials: {
                        "Mild Steel": "S235, S355, A36, A572",
                        "Stainless Steel": "304, 316, 310, 321",
                        "Aluminium": "5083, 6082, 5052",
                        "Wear Plate": "Hardox 400/500, AR400/500"
                    }
                }
            },
            profile: {
                title: "Profile Cutting Services",
                desc: "Heavy-duty oxy-fuel profile cutting for thick carbon steel sections, base plates, and structural components used in bridges, buildings, and heavy machinery.",
                model3d: "https://modelviewer.dev/shared-assets/models/Astronaut.glb",
                modelSize: "3.8 MB",
                polygons: "28,945",
                features: [
                    "Extreme thickness capability (300mm+)",
                    "Structural integrity preservation",
                    "Massive scale capacity",
                    "Precision oxy-fuel technology",
                    "Straightness within 1mm per meter"
                ],
                specs: {
                    general: {
                        "Max Thickness": "350mm (14\") carbon steel",
                        "Width Capacity": "Up to 4000mm (13')",
                        "Accuracy": "± 2mm (± 0.080\")",
                        "Beveling": "Available up to 30 degrees",
                        "Surface Finish": "As-cut or machined"
                    },
                    materials: {
                        "Structural Steel": "S275, S355, A992",
                        "Pressure Vessel": "A516 Grade 70, A537",
                        "Marine Grade": "Grade A, AH32, DH36",
                        "Hardness": "Consistent through-cut up to 400 HB"
                    }
                }
            }
        };

        // 3D Model Control Functions
        function resetModelView(type = 'product') {
            const viewerId = type === 'hero' ? 'hero-model-viewer' : 'product-model-viewer';
            const modelViewer = document.getElementById(viewerId);
            if (modelViewer) {
                modelViewer.resetTurntableRotation();
                modelViewer.cameraOrbit = '0deg 75deg 105%';
                modelViewer.fieldOfView = '30deg';
                showNotification('Model view reset', 'success');
            }
        }

        function toggleAutoRotate(type = 'product') {
            const viewerId = type === 'hero' ? 'hero-model-viewer' : 'product-model-viewer';
            const modelViewer = document.getElementById(viewerId);
            if (modelViewer) {
                modelViewer.autoRotate = !modelViewer.autoRotate;
                const button = event.target.closest('button');
                if (button) {
                    const icon = button.querySelector('i');
                    if (icon) {
                        icon.className = modelViewer.autoRotate ? 'fas fa-pause' : 'fas fa-play';
                    }
                    button.querySelector('span').textContent = modelViewer.autoRotate ? ' Stop Rotate' : ' Auto Rotate';
                }
                showNotification(`Auto-rotate ${modelViewer.autoRotate ? 'enabled' : 'disabled'}`, 'info');
            }
        }

        function downloadCurrentModel() {
            const currentProduct = getCurrentProduct();
            if (currentProduct && currentProduct.title) {
                showNotification(`Preparing ${currentProduct.title} CAD files for download...`, 'info');
                // In production, this would trigger actual file download
                setTimeout(() => {
                    showNotification(`${currentProduct.title} CAD files ready for download`, 'success');
                    // Simulate download
                    const link = document.createElement('a');
                    link.href = currentProduct.model3d;
                    link.download = `${currentProduct.title.replace(/\s+/g, '_')}.glb`;
                    link.click();
                }, 1500);
            }
        }

        function downloadHeroModel() {
            showNotification('Downloading hero model CAD files...', 'info');
            setTimeout(() => {
                showNotification('Hero model CAD files downloaded', 'success');
            }, 1500);
        }

        function takeScreenshot() {
            const modelViewer = document.getElementById('product-model-viewer');
            if (modelViewer) {
                modelViewer.takeScreenshot().then((blob) => {
                    const link = document.createElement('a');
                    link.href = URL.createObjectURL(blob);
                    link.download = '3d-model-screenshot.png';
                    link.click();
                    showNotification('Screenshot saved!', 'success');
                });
            }
        }

        function showMeasurementTools() {
            showNotification('Measurement tools activated. Click on points to measure distances.', 'info');
            // In a real implementation, you would add measurement functionality here
        }

        function showCrossSection() {
            const modelViewer = document.getElementById('product-model-viewer');
            if (modelViewer) {
                // Toggle cross-section
                const currentX = modelViewer.getAttribute('cross-section-x') || '0';
                const newX = currentX === '0' ? '0.5' : '0';
                modelViewer.setAttribute('cross-section-x', newX);
                showNotification(`Cross-section ${newX === '0' ? 'hidden' : 'shown'}`, 'info');
            }
        }

        function showAllModels() {
            // Scroll to 3D gallery section
            document.getElementById('3d-gallery').scrollIntoView({ 
                behavior: 'smooth',
                block: 'start'
            });
            showNotification('Viewing all 3D models gallery', 'info');
        }

        function showNotification(message, type = 'info') {
            // Create notification element
            const notification = document.createElement('div');
            notification.className = `fixed top-4 right-4 z-50 px-6 py-3 rounded-lg shadow-lg text-white font-medium transform transition-all duration-300 ${
                type === 'success' ? 'bg-green-600' : 
                type === 'error' ? 'bg-red-600' : 
                'bg-blue-600'
            }`;
            notification.innerHTML = `
                <div class="flex items-center gap-2">
                    <i class="fas fa-${type === 'success' ? 'check-circle' : type === 'error' ? 'exclamation-circle' : 'info-circle'}"></i>
                    <span>${message}</span>
                </div>
            `;
            
            document.body.appendChild(notification);
            
            // Remove after 3 seconds
            setTimeout(() => {
                notification.style.transform = 'translateX(100%)';
                setTimeout(() => notification.remove(), 300);
            }, 3000);
        }

        function getCurrentProduct() {
            const activeChip = document.querySelector('.flange-chip.active');
            if (activeChip) {
                const chipId = activeChip.id.replace('chip-', '');
                return productData[chipId];
            }
            return productData.wnf;
        }

        function updateProduct(key) {
            const data = productData[key] || productData.wnf;
            
            // Update active chip
            document.querySelectorAll('.flange-chip').forEach(c => c.classList.remove('active'));
            const activeChip = document.getElementById(`chip-${key}`);
            if (activeChip) activeChip.classList.add('active');

            // Update 3D Model in product viewer
            const productModelViewer = document.getElementById('product-model-viewer');
            if (productModelViewer && data.model3d) {
                productModelViewer.src = data.model3d;
                productModelViewer.alt = data.title;
                
                // Update model info
                document.getElementById('current-model-name').textContent = data.title;
                document.getElementById('model-size').textContent = data.modelSize || '~2.5 MB';
                document.getElementById('model-polygons').textContent = data.polygons || '15,428';
            }

            // Update product details
            document.getElementById('p-title').innerText = data.title;
            document.getElementById('p-desc').innerText = data.desc;
            
            // Update features with staggered animation
            const featuresContainer = document.getElementById('p-features');
            featuresContainer.innerHTML = data.features.map((f, i) => `
                <div class="feature-card p-5 rounded-2xl opacity-100 reveal stagger-delay-${i % 4}">
                    <div class="flex items-start gap-4">
                        <div class="mt-1 w-8 h-8 bg-blue-600 rounded-lg flex items-center justify-center flex-shrink-0">
                            <i class="fas fa-check text-white text-sm"></i>
                        </div>
                        <span class="text-slate-700 font-semibold">${f}</span>
                    </div>
                </div>
            `).join('');

            // Update specifications
            document.getElementById('spec-title').innerText = `${data.title} - Technical Specifications`;
            renderSpecTables(data.specs);
            
            // Animate product card
            const productCard = document.getElementById('product-card');
            productCard.style.opacity = '0';
            productCard.style.transform = 'translateY(20px)';
            setTimeout(() => {
                productCard.style.opacity = '1';
                productCard.style.transform = 'translateY(0)';
                initReveal(); // Re-initialize reveal for new elements
                
                // Scroll to product section
                document.getElementById('products').scrollIntoView({ 
                    behavior: 'smooth',
                    block: 'start'
                });
            }, 50);
            
            showNotification(`Loaded ${data.title} 3D model`, 'success');
        }

        function renderSpecTables(specs) {
            const container = document.getElementById('spec-tables-container');
            container.innerHTML = ''; 

            const categories = [
                { id: 'general', label: 'Attribute', valueLabel: 'Detail / Capability', icon: 'fas fa-ruler-combined' },
                { id: 'materials', label: 'Material Grade', valueLabel: 'ASTM / ASME / EN Specifications', icon: 'fas fa-weight' }
            ];

            categories.forEach(cat => {
                const tableData = specs[cat.id];
                if (!tableData) return;

                const tableHTML = `
                    <div class="overflow-hidden rounded-2xl border border-slate-800 bg-slate-900/50">
                        <div class="bg-slate-800/70 px-6 py-4 border-b border-slate-700 flex items-center gap-3">
                            <i class="${cat.icon} text-blue-400"></i>
                            <h3 class="font-bold text-lg">${cat.id === 'general' ? 'General Specifications' : 'Material Grades'}</h3>
                        </div>
                        <div class="overflow-x-auto">
                            <table class="w-full spec-table">
                                <thead class="bg-slate-800/40 text-blue-300 text-xs uppercase tracking-widest font-bold">
                                    <tr>
                                        <th class="px-6 py-4 text-left">${cat.label}</th>
                                        <th class="px-6 py-4 text-left">${cat.valueLabel}</th>
                                    </tr>
                                </thead>
                                <tbody class="divide-y divide-slate-800 text-sm">
                                    ${Object.entries(tableData).map(([attr, detail], index) => `
                                        <tr class="${index % 2 === 0 ? 'bg-slate-900/20' : ''}">
                                            <td class="px-6 py-4 font-semibold text-slate-300">${attr}</td>
                                            <td class="px-6 py-4 text-slate-400">${detail}</td>
                                        </tr>
                                    `).join('')}
                                </tbody>
                            </table>
                        </div>
                    </div>
                `;
                container.innerHTML += tableHTML;
            });
        }

        function handleSearch(query) {
            const term = query.toLowerCase().trim();
            if (term.length < 2) return;
            
            // Search in titles and keys
            for (const [key, data] of Object.entries(productData)) {
                if (data.title.toLowerCase().includes(term) || 
                    key.includes(term) || 
                    data.desc.toLowerCase().includes(term) ||
                    data.features.some(f => f.toLowerCase().includes(term))) {
                    updateProduct(key);
                    break;
                }
            }
        }

        function initReveal() {
            const reveals = document.querySelectorAll('.reveal');
            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.classList.add('active');
                    }
                });
            }, { 
                threshold: 0.1,
                rootMargin: '0px 0px -50px 0px'
            });
            reveals.forEach(r => observer.observe(r));
        }

        // Initialize 3D model controls
        function init3DControls() {
            // Rotation speed control
            const rotationSlider = document.getElementById('rotation-speed');
            if (rotationSlider) {
                rotationSlider.addEventListener('input', function(e) {
                    const modelViewer = document.getElementById('product-model-viewer');
                    if (modelViewer) {
                        const speed = parseFloat(e.target.value);
                        modelViewer.autoRotateDelay = 0;
                        modelViewer.autoRotate = speed > 0;
                        if (speed > 0) {
                            modelViewer.autoRotateSpeed = `${speed * 10}deg`;
                        }
                    }
                });
            }

            // Zoom level control
            const zoomSlider = document.getElementById('zoom-level');
            if (zoomSlider) {
                zoomSlider.addEventListener('input', function(e) {
                    const modelViewer = document.getElementById('product-model-viewer');
                    if (modelViewer) {
                        const zoom = parseInt(e.target.value);
                        const fov = 60 - (zoom * 3);
                        modelViewer.fieldOfView = `${Math.max(10, fov)}deg`;
                    }
                });
            }
        }

        // Initialize
        window.onload = () => {
            updateProduct('wnf');
            initReveal();
            init3DControls();
            
            // Close mobile menu when clicking outside
            document.addEventListener('click', (e) => {
                const mobileMenu = document.getElementById('mobile-menu');
                const menuBtn = document.querySelector('button[onclick="toggleMobileMenu()"]');
                
                if (mobileMenu && mobileMenu.classList.contains('active') && 
                    !mobileMenu.contains(e.target) && 
                    menuBtn && !menuBtn.contains(e.target)) {
                    mobileMenu.classList.remove('active');
                }
            });
            
            // Close order modal on escape key
            document.addEventListener('keydown', (e) => {
                if (e.key === 'Escape') {
                    const orderModal = document.getElementById('order-modal');
                    if (orderModal && !orderModal.classList.contains('hidden')) {
                        closeOrderModal();
                    }
                }
            });
            
            // Initialize order modal with current product
            document.getElementById('order-product').addEventListener('change', function() {
                const selectedValue = this.value;
                if (selectedValue && selectedValue !== 'custom') {
                    const product = productData[selectedValue];
                    if (product) {
                        document.getElementById('order-material').value = 'stainless';
                    }
                }
            });
            
            // Initialize all gallery model viewers
            const galleryViewers = document.querySelectorAll('#3d-gallery model-viewer');
            galleryViewers.forEach(viewer => {
                viewer.addEventListener('click', function() {
                    const productKey = this.closest('.bg-slate-50').querySelector('button').onclick
                        .toString().match(/updateProduct\('(\w+)'\)/)[1];
                    if (productKey) {
                        updateProduct(productKey);
                    }
                });
            });
        };
    </script>
</body>
</html>
