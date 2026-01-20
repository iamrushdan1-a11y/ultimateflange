<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ultimate Flange | Industrial Precision Solutions</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        :root {
            --primary-blue: #1e40af;
            --secondary-blue: #3b82f6;
            --accent-blue: #60a5fa;
            --primary-green: #10b981;
            --primary-orange: #f59e0b;
            --primary-purple: #8b5cf6;
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
        
        /* Dashboard Styles */
        .dashboard-grid {
            display: grid;
            grid-template-columns: 280px 1fr;
            min-height: calc(100vh - 80px);
        }
        
        .sidebar {
            background: linear-gradient(180deg, #1e293b 0%, #0f172a 100%);
            color: white;
        }
        
        .sidebar-menu-item {
            display: flex;
            align-items: center;
            gap: 12px;
            padding: 14px 20px;
            border-radius: 8px;
            transition: all 0.3s ease;
            color: #cbd5e1;
            font-weight: 500;
        }
        
        .sidebar-menu-item:hover, .sidebar-menu-item.active {
            background: rgba(255, 255, 255, 0.1);
            color: white;
            transform: translateX(5px);
        }
        
        .dashboard-card {
            background: white;
            border-radius: 12px;
            padding: 1.5rem;
            box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
            border: 1px solid #e2e8f0;
            transition: all 0.3s ease;
        }
        
        .dashboard-card:hover {
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
            transform: translateY(-2px);
        }
        
        .stat-card {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border-radius: 12px;
            padding: 1.5rem;
        }
        
        .stat-card.sales {
            background: linear-gradient(135deg, #4ade80 0%, #22c55e 100%);
        }
        
        .stat-card.orders {
            background: linear-gradient(135deg, #fbbf24 0%, #f59e0b 100%);
        }
        
        .stat-card.customers {
            background: linear-gradient(135deg, #8b5cf6 0%, #7c3aed 100%);
        }
        
        .progress-bar {
            height: 8px;
            background: #e2e8f0;
            border-radius: 4px;
            overflow: hidden;
        }
        
        .progress-fill {
            height: 100%;
            border-radius: 4px;
            background: linear-gradient(90deg, #3b82f6 0%, #1d4ed8 100%);
            transition: width 1s ease;
        }
        
        .table-container {
            overflow-x: auto;
            border-radius: 8px;
            border: 1px solid #e2e8f0;
        }
        
        .table-container table {
            min-width: 100%;
        }
        
        .table-container th {
            background: #f8fafc;
            font-weight: 600;
            color: #475569;
            text-transform: uppercase;
            font-size: 0.75rem;
            letter-spacing: 0.05em;
            padding: 12px 16px;
            border-bottom: 1px solid #e2e8f0;
        }
        
        .table-container td {
            padding: 16px;
            border-bottom: 1px solid #e2e8f0;
            color: #475569;
        }
        
        .table-container tr:hover td {
            background: #f1f5f9;
        }
        
        .badge {
            display: inline-flex;
            align-items: center;
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 0.75rem;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 0.05em;
        }
        
        .badge-success {
            background: #dcfce7;
            color: #166534;
        }
        
        .badge-warning {
            background: #fef3c7;
            color: #92400e;
        }
        
        .badge-danger {
            background: #fee2e2;
            color: #991b1b;
        }
        
        .badge-info {
            background: #dbeafe;
            color: #1e40af;
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
        
        /* Hero Image Container */
        .hero-image-container {
            width: 100%;
            height: 400px;
            border-radius: 16px;
            overflow: hidden;
            background: linear-gradient(135deg, #f8fafc 0%, #e2e8f0 100%);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
            position: relative;
        }
        
        .hero-image-container img {
            width: 100%;
            height: 100%;
            object-fit: cover;
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
        
        /* Product Thumbnails */
        .product-thumbnail {
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
        
        .product-thumbnail:hover {
            transform: translateY(-4px);
            box-shadow: 0 12px 24px rgba(0, 0, 0, 0.1);
        }
        
        .product-thumbnail img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        
        .product-placeholder {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            color: #64748b;
        }
        
        .product-placeholder i {
            font-size: 48px;
            margin-bottom: 12px;
            color: #94a3b8;
        }
        
        /* Product Image Container */
        .product-image-container {
            width: 100%;
            height: 400px;
            border-radius: 16px;
            overflow: hidden;
            background: linear-gradient(135deg, #f8fafc 0%, #e2e8f0 100%);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
            position: relative;
        }
        
        .product-image-container img {
            width: 100%;
            height: 100%;
            object-fit: contain;
            background: #f8fafc;
        }
        
        /* Gallery Product Cards */
        .gallery-product-card {
            height: 100%;
            transition: all 0.3s ease;
        }
        
        .gallery-product-card:hover {
            transform: translateY(-8px);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
        }
        
        /* Tabs */
        .tab-button {
            padding: 12px 24px;
            border: none;
            background: none;
            font-weight: 500;
            color: #64748b;
            border-bottom: 2px solid transparent;
            transition: all 0.3s ease;
            cursor: pointer;
        }
        
        .tab-button.active {
            color: #3b82f6;
            border-bottom-color: #3b82f6;
        }
        
        .tab-content {
            display: none;
        }
        
        .tab-content.active {
            display: block;
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
                        <input type="password" id="login-password" required placeholder="••••••••" 
                               class="w-full px-5 py-3.5 rounded-xl border-2 border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none transition">
                    </div>
                    <div class="flex items-center justify-between">
                        <label class="flex items-center">
                            <input type="checkbox" class="rounded border-slate-300 text-blue-600 focus:ring-blue-500">
                            <span class="ml-2 text-sm text-slate-600">Remember me</span>
                        </label>
                        <a href="#" class="text-sm text-blue-600 font-medium hover:text-blue-800">Forgot password?</a>
                    </div>
                    
                    <!-- User Type Selection -->
                    <div>
                        <label class="block text-sm font-semibold text-slate-700 mb-2">Login As</label>
                        <div class="grid grid-cols-2 gap-3">
                            <button type="button" onclick="setUserType('partner')" 
                                    class="px-4 py-3 rounded-lg border-2 border-blue-200 bg-blue-50 text-blue-700 font-medium flex items-center justify-center gap-2">
                                <i class="fas fa-user-shield"></i>
                                Partner
                            </button>
                            <button type="button" onclick="setUserType('supplier')" 
                                    class="px-4 py-3 rounded-lg border-2 border-slate-200 hover:border-blue-200 hover:bg-blue-50 font-medium flex items-center justify-center gap-2">
                                <i class="fas fa-building"></i>
                                Supplier
                            </button>
                        </div>
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

    <!-- Dashboard Modal (Only for Supplier Accounts) -->
    <div id="dashboard-modal" class="fixed inset-0 bg-black/60 backdrop-blur-md hidden items-center justify-center p-4 z-50">
        <div class="bg-white w-full max-w-7xl h-[90vh] rounded-3xl shadow-2xl overflow-hidden relative flex flex-col">
            <div class="px-8 pt-8 pb-4 border-b border-slate-200">
                <div class="flex justify-between items-center">
                    <div>
                        <h2 class="text-3xl font-bold text-slate-900">Supplier Dashboard</h2>
                        <p class="text-slate-600 mt-1">Manage your orders, inventory, and customer interactions</p>
                    </div>
                    <div class="flex items-center gap-4">
                        <div class="relative group">
                            <button class="w-10 h-10 rounded-full bg-slate-100 flex items-center justify-center text-slate-700 hover:bg-slate-200 transition">
                                <i class="fas fa-bell"></i>
                            </button>
                            <span class="absolute top-0 right-0 w-3 h-3 bg-red-500 rounded-full border-2 border-white"></span>
                        </div>
                        <button onclick="closeDashboard()" class="text-slate-400 hover:text-slate-700">
                            <i class="fas fa-times text-2xl"></i>
                        </button>
                    </div>
                </div>
                
                <!-- Dashboard Tabs -->
                <div class="flex gap-1 mt-6 border-b border-slate-200">
                    <button onclick="switchDashboardTab('overview')" class="tab-button active">
                        <i class="fas fa-chart-bar mr-2"></i>Overview
                    </button>
                    <button onclick="switchDashboardTab('orders')" class="tab-button">
                        <i class="fas fa-shopping-cart mr-2"></i>Orders
                    </button>
                    <button onclick="switchDashboardTab('inventory')" class="tab-button">
                        <i class="fas fa-boxes mr-2"></i>Inventory
                    </button>
                    <button onclick="switchDashboardTab('customers')" class="tab-button">
                        <i class="fas fa-users mr-2"></i>Customers
                    </button>
                    <button onclick="switchDashboardTab('analytics')" class="tab-button">
                        <i class="fas fa-chart-line mr-2"></i>Analytics
                    </button>
                    <button onclick="switchDashboardTab('settings')" class="tab-button">
                        <i class="fas fa-cog mr-2"></i>Settings
                    </button>
                </div>
            </div>
            
            <!-- Dashboard Content -->
            <div class="flex-1 overflow-auto p-8">
                <!-- Overview Tab -->
                <div id="dashboard-overview" class="tab-content active space-y-8">
                    <!-- Stats Cards -->
                    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
                        <div class="stat-card sales">
                            <div class="flex justify-between items-start">
                                <div>
                                    <p class="text-sm opacity-90">Total Revenue</p>
                                    <h3 class="text-3xl font-bold mt-2">₹2,847,500</h3>
                                    <p class="text-sm mt-2 flex items-center">
                                        <i class="fas fa-arrow-up mr-1"></i> 12.5% from last month
                                    </p>
                                </div>
                                <div class="w-12 h-12 bg-white/20 rounded-lg flex items-center justify-center">
                                    <i class="fas fa-rupee-sign text-2xl"></i>
                                </div>
                            </div>
                        </div>
                        
                        <div class="stat-card orders">
                            <div class="flex justify-between items-start">
                                <div>
                                    <p class="text-sm opacity-90">Active Orders</p>
                                    <h3 class="text-3xl font-bold mt-2">47</h3>
                                    <p class="text-sm mt-2 flex items-center">
                                        <i class="fas fa-clock mr-1"></i> 8 pending approval
                                    </p>
                                </div>
                                <div class="w-12 h-12 bg-white/20 rounded-lg flex items-center justify-center">
                                    <i class="fas fa-shopping-cart text-2xl"></i>
                                </div>
                            </div>
                        </div>
                        
                        <div class="stat-card customers">
                            <div class="flex justify-between items-start">
                                <div>
                                    <p class="text-sm opacity-90">Active Customers</p>
                                    <h3 class="text-3xl font-bold mt-2">156</h3>
                                    <p class="text-sm mt-2 flex items-center">
                                        <i class="fas fa-user-plus mr-1"></i> +12 this month
                                    </p>
                                </div>
                                <div class="w-12 h-12 bg-white/20 rounded-lg flex items-center justify-center">
                                    <i class="fas fa-users text-2xl"></i>
                                </div>
                            </div>
                        </div>
                        
                        <div class="stat-card">
                            <div class="flex justify-between items-start">
                                <div>
                                    <p class="text-sm opacity-90">Inventory Value</p>
                                    <h3 class="text-3xl font-bold mt-2">₹5,620,000</h3>
                                    <p class="text-sm mt-2 flex items-center">
                                        <i class="fas fa-box mr-1"></i> 87 items in stock
                                    </p>
                                </div>
                                <div class="w-12 h-12 bg-white/20 rounded-lg flex items-center justify-center">
                                    <i class="fas fa-warehouse text-2xl"></i>
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Charts and Recent Orders -->
                    <div class="grid lg:grid-cols-2 gap-8">
                        <!-- Sales Chart -->
                        <div class="dashboard-card">
                            <h3 class="font-bold text-lg text-slate-900 mb-4">Revenue Trend</h3>
                            <div class="h-64">
                                <canvas id="salesChart"></canvas>
                            </div>
                        </div>
                        
                        <!-- Recent Orders -->
                        <div class="dashboard-card">
                            <div class="flex justify-between items-center mb-4">
                                <h3 class="font-bold text-lg text-slate-900">Recent Orders</h3>
                                <a href="#" class="text-blue-600 text-sm font-medium hover:text-blue-800">View All</a>
                            </div>
                            <div class="space-y-4">
                                <div class="flex items-center justify-between p-3 bg-slate-50 rounded-lg">
                                    <div>
                                        <div class="font-medium">#ORD-7842</div>
                                        <div class="text-sm text-slate-500">Weld Neck Flange</div>
                                    </div>
                                    <div class="text-right">
                                        <div class="font-medium">₹245,000</div>
                                        <span class="badge badge-warning">Processing</span>
                                    </div>
                                </div>
                                <div class="flex items-center justify-between p-3 bg-slate-50 rounded-lg">
                                    <div>
                                        <div class="font-medium">#ORD-7841</div>
                                        <div class="text-sm text-slate-500">Long Weld Neck</div>
                                    </div>
                                    <div class="text-right">
                                        <div class="font-medium">₹187,500</div>
                                        <span class="badge badge-success">Shipped</span>
                                    </div>
                                </div>
                                <div class="flex items-center justify-between p-3 bg-slate-50 rounded-lg">
                                    <div>
                                        <div class="font-medium">#ORD-7840</div>
                                        <div class="text-sm text-slate-500">Blind Flange</div>
                                    </div>
                                    <div class="text-right">
                                        <div class="font-medium">₹92,300</div>
                                        <span class="badge badge-danger">Pending</span>
                                    </div>
                                </div>
                                <div class="flex items-center justify-between p-3 bg-slate-50 rounded-lg">
                                    <div>
                                        <div class="font-medium">#ORD-7839</div>
                                        <div class="text-sm text-slate-500">Plasma CNC Cutting</div>
                                    </div>
                                    <div class="text-right">
                                        <div class="font-medium">₹315,800</div>
                                        <span class="badge badge-info">Approved</span>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Quick Stats -->
                    <div class="grid md:grid-cols-3 gap-6">
                        <div class="dashboard-card">
                            <h3 class="font-bold text-lg text-slate-900 mb-4">Order Status</h3>
                            <div class="space-y-3">
                                <div>
                                    <div class="flex justify-between mb-1">
                                        <span class="text-sm">Pending Approval</span>
                                        <span class="text-sm font-medium">8</span>
                                    </div>
                                    <div class="progress-bar">
                                        <div class="progress-fill" style="width: 17%"></div>
                                    </div>
                                </div>
                                <div>
                                    <div class="flex justify-between mb-1">
                                        <span class="text-sm">In Production</span>
                                        <span class="text-sm font-medium">15</span>
                                    </div>
                                    <div class="progress-bar">
                                        <div class="progress-fill" style="width: 32%"></div>
                                    </div>
                                </div>
                                <div>
                                    <div class="flex justify-between mb-1">
                                        <span class="text-sm">Ready to Ship</span>
                                        <span class="text-sm font-medium">12</span>
                                    </div>
                                    <div class="progress-bar">
                                        <div class="progress-fill" style="width: 26%"></div>
                                    </div>
                                </div>
                                <div>
                                    <div class="flex justify-between mb-1">
                                        <span class="text-sm">Delivered</span>
                                        <span class="text-sm font-medium">12</span>
                                    </div>
                                    <div class="progress-bar">
                                        <div class="progress-fill" style="width: 26%"></div>
                                    </div>
                                </div>
                            </div>
                        </div>
                        
                        <div class="dashboard-card">
                            <h3 class="font-bold text-lg text-slate-900 mb-4">Top Products</h3>
                            <div class="space-y-3">
                                <div class="flex items-center justify-between">
                                    <div class="flex items-center gap-3">
                                        <div class="w-10 h-10 bg-blue-100 rounded-lg flex items-center justify-center">
                                            <i class="fas fa-fire text-blue-600"></i>
                                        </div>
                                        <div>
                                            <div class="font-medium">Weld Neck Flange</div>
                                            <div class="text-sm text-slate-500">₹1.2M revenue</div>
                                        </div>
                                    </div>
                                    <div class="text-lg font-bold">42%</div>
                                </div>
                                <div class="flex items-center justify-between">
                                    <div class="flex items-center gap-3">
                                        <div class="w-10 h-10 bg-green-100 rounded-lg flex items-center justify-center">
                                            <i class="fas fa-ruler-vertical text-green-600"></i>
                                        </div>
                                        <div>
                                            <div class="font-medium">Long Weld Neck</div>
                                            <div class="text-sm text-slate-500">₹850K revenue</div>
                                        </div>
                                    </div>
                                    <div class="text-lg font-bold">30%</div>
                                </div>
                                <div class="flex items-center justify-between">
                                    <div class="flex items-center gap-3">
                                        <div class="w-10 h-10 bg-purple-100 rounded-lg flex items-center justify-center">
                                            <i class="fas fa-bolt text-purple-600"></i>
                                        </div>
                                        <div>
                                            <div class="font-medium">Plasma CNC</div>
                                            <div class="text-sm text-slate-500">₹620K revenue</div>
                                        </div>
                                    </div>
                                    <div class="text-lg font-bold">22%</div>
                                </div>
                            </div>
                        </div>
                        
                        <div class="dashboard-card">
                            <h3 class="font-bold text-lg text-slate-900 mb-4">Quick Actions</h3>
                            <div class="space-y-3">
                                <button class="w-full py-3 bg-blue-50 text-blue-700 rounded-lg font-medium hover:bg-blue-100 transition flex items-center justify-center gap-2">
                                    <i class="fas fa-plus"></i> Add New Product
                                </button>
                                <button class="w-full py-3 bg-green-50 text-green-700 rounded-lg font-medium hover:bg-green-100 transition flex items-center justify-center gap-2">
                                    <i class="fas fa-file-invoice"></i> Create Invoice
                                </button>
                                <button class="w-full py-3 bg-purple-50 text-purple-700 rounded-lg font-medium hover:bg-purple-100 transition flex items-center justify-center gap-2">
                                    <i class="fas fa-chart-bar"></i> Generate Report
                                </button>
                                <button class="w-full py-3 bg-orange-50 text-orange-700 rounded-lg font-medium hover:bg-orange-100 transition flex items-center justify-center gap-2">
                                    <i class="fas fa-box"></i> Update Inventory
                                </button>
                            </div>
                        </div>
                    </div>
                </div>
                
                <!-- Orders Tab -->
                <div id="dashboard-orders" class="tab-content hidden">
                    <div class="flex justify-between items-center mb-6">
                        <h3 class="text-2xl font-bold text-slate-900">Order Management</h3>
                        <button class="px-4 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition flex items-center gap-2">
                            <i class="fas fa-plus"></i> New Order
                        </button>
                    </div>
                    
                    <div class="table-container">
                        <table class="w-full">
                            <thead>
                                <tr>
                                    <th>Order ID</th>
                                    <th>Customer</th>
                                    <th>Product</th>
                                    <th>Quantity</th>
                                    <th>Amount</th>
                                    <th>Status</th>
                                    <th>Date</th>
                                    <th>Actions</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr>
                                    <td class="font-medium">#ORD-7842</td>
                                    <td>Oil & Gas Corp</td>
                                    <td>Weld Neck Flange</td>
                                    <td>50</td>
                                    <td class="font-bold">₹245,000</td>
                                    <td><span class="badge badge-warning">Processing</span></td>
                                    <td>2024-03-15</td>
                                    <td>
                                        <button class="text-blue-600 hover:text-blue-800 mr-3">
                                            <i class="fas fa-eye"></i>
                                        </button>
                                        <button class="text-green-600 hover:text-green-800">
                                            <i class="fas fa-edit"></i>
                                        </button>
                                    </td>
                                </tr>
                                <tr>
                                    <td class="font-medium">#ORD-7841</td>
                                    <td>PowerGen Ltd</td>
                                    <td>Long Weld Neck</td>
                                    <td>25</td>
                                    <td class="font-bold">₹187,500</td>
                                    <td><span class="badge badge-success">Shipped</span></td>
                                    <td>2024-03-14</td>
                                    <td>
                                        <button class="text-blue-600 hover:text-blue-800 mr-3">
                                            <i class="fas fa-eye"></i>
                                        </button>
                                        <button class="text-green-600 hover:text-green-800">
                                            <i class="fas fa-edit"></i>
                                        </button>
                                    </td>
                                </tr>
                                <tr>
                                    <td class="font-medium">#ORD-7840</td>
                                    <td>Marine Solutions</td>
                                    <td>Blind Flange</td>
                                    <td>100</td>
                                    <td class="font-bold">₹92,300</td>
                                    <td><span class="badge badge-danger">Pending</span></td>
                                    <td>2024-03-13</td>
                                    <td>
                                        <button class="text-blue-600 hover:text-blue-800 mr-3">
                                            <i class="fas fa-eye"></i>
                                        </button>
                                        <button class="text-green-600 hover:text-green-800">
                                            <i class="fas fa-edit"></i>
                                        </button>
                                    </td>
                                </tr>
                                <tr>
                                    <td class="font-medium">#ORD-7839</td>
                                    <td>Chemical Process</td>
                                    <td>Plasma CNC Cutting</td>
                                    <td>1</td>
                                    <td class="font-bold">₹315,800</td>
                                    <td><span class="badge badge-info">Approved</span></td>
                                    <td>2024-03-12</td>
                                    <td>
                                        <button class="text-blue-600 hover:text-blue-800 mr-3">
                                            <i class="fas fa-eye"></i>
                                        </button>
                                        <button class="text-green-600 hover:text-green-800">
                                            <i class="fas fa-edit"></i>
                                        </button>
                                    </td>
                                </tr>
                                <tr>
                                    <td class="font-medium">#ORD-7838</td>
                                    <td>Construction Co</td>
                                    <td>Slip-On Flange</td>
                                    <td>200</td>
                                    <td class="font-bold">₹156,400</td>
                                    <td><span class="badge badge-success">Delivered</span></td>
                                    <td>2024-03-10</td>
                                    <td>
                                        <button class="text-blue-600 hover:text-blue-800 mr-3">
                                            <i class="fas fa-eye"></i>
                                        </button>
                                        <button class="text-green-600 hover:text-green-800">
                                            <i class="fas fa-edit"></i>
                                        </button>
                                    </td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
                
                <!-- Inventory Tab -->
                <div id="dashboard-inventory" class="tab-content hidden">
                    <div class="flex justify-between items-center mb-6">
                        <h3 class="text-2xl font-bold text-slate-900">Inventory Management</h3>
                        <button class="px-4 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition flex items-center gap-2">
                            <i class="fas fa-plus"></i> Add Stock
                        </button>
                    </div>
                    
                    <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-6 mb-8">
                        <div class="dashboard-card">
                            <div class="flex items-center justify-between">
                                <div>
                                    <div class="text-sm text-slate-500">Total Items</div>
                                    <div class="text-3xl font-bold mt-1">87</div>
                                </div>
                                <div class="w-12 h-12 bg-blue-100 rounded-lg flex items-center justify-center">
                                    <i class="fas fa-boxes text-blue-600 text-xl"></i>
                                </div>
                            </div>
                        </div>
                        <div class="dashboard-card">
                            <div class="flex items-center justify-between">
                                <div>
                                    <div class="text-sm text-slate-500">Low Stock Items</div>
                                    <div class="text-3xl font-bold mt-1">12</div>
                                </div>
                                <div class="w-12 h-12 bg-red-100 rounded-lg flex items-center justify-center">
                                    <i class="fas fa-exclamation-triangle text-red-600 text-xl"></i>
                                </div>
                            </div>
                        </div>
                        <div class="dashboard-card">
                            <div class="flex items-center justify-between">
                                <div>
                                    <div class="text-sm text-slate-500">Out of Stock</div>
                                    <div class="text-3xl font-bold mt-1">3</div>
                                </div>
                                <div class="w-12 h-12 bg-orange-100 rounded-lg flex items-center justify-center">
                                    <i class="fas fa-times-circle text-orange-600 text-xl"></i>
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <div class="table-container">
                        <table class="w-full">
                            <thead>
                                <tr>
                                    <th>Product</th>
                                    <th>SKU</th>
                                    <th>Current Stock</th>
                                    <th>Reorder Level</th>
                                    <th>Value</th>
                                    <th>Status</th>
                                    <th>Actions</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr>
                                    <td class="font-medium">Weld Neck Flange DN50</td>
                                    <td>SKU-WNF-50</td>
                                    <td>250</td>
                                    <td>100</td>
                                    <td class="font-bold">₹1,250,000</td>
                                    <td><span class="badge badge-success">In Stock</span></td>
                                    <td>
                                        <button class="text-blue-600 hover:text-blue-800 mr-3">
                                            <i class="fas fa-edit"></i>
                                        </button>
                                        <button class="text-red-600 hover:text-red-800">
                                            <i class="fas fa-trash"></i>
                                        </button>
                                    </td>
                                </tr>
                                <tr>
                                    <td class="font-medium">Long Weld Neck DN100</td>
                                    <td>SKU-LWN-100</td>
                                    <td>85</td>
                                    <td>50</td>
                                    <td class="font-bold">₹850,000</td>
                                    <td><span class="badge badge-warning">Low Stock</span></td>
                                    <td>
                                        <button class="text-blue-600 hover:text-blue-800 mr-3">
                                            <i class="fas fa-edit"></i>
                                        </button>
                                        <button class="text-red-600 hover:text-red-800">
                                            <i class="fas fa-trash"></i>
                                        </button>
                                    </td>
                                </tr>
                                <tr>
                                    <td class="font-medium">Blind Flange DN80</td>
                                    <td>SKU-BF-80</td>
                                    <td>0</td>
                                    <td>25</td>
                                    <td class="font-bold">₹0</td>
                                    <td><span class="badge badge-danger">Out of Stock</span></td>
                                    <td>
                                        <button class="text-blue-600 hover:text-blue-800 mr-3">
                                            <i class="fas fa-edit"></i>
                                        </button>
                                        <button class="text-red-600 hover:text-red-800">
                                            <i class="fas fa-trash"></i>
                                        </button>
                                    </td>
                                </tr>
                                <tr>
                                    <td class="font-medium">Slip-On Flange DN40</td>
                                    <td>SKU-SOF-40</td>
                                    <td>120</td>
                                    <td>75</td>
                                    <td class="font-bold">₹480,000</td>
                                    <td><span class="badge badge-success">In Stock</span></td>
                                    <td>
                                        <button class="text-blue-600 hover:text-blue-800 mr-3">
                                            <i class="fas fa-edit"></i>
                                        </button>
                                        <button class="text-red-600 hover:text-red-800">
                                            <i class="fas fa-trash"></i>
                                        </button>
                                    </td>
                                </tr>
                                <tr>
                                    <td class="font-medium">Puddle Flange DN150</td>
                                    <td>SKU-PF-150</td>
                                    <td>45</td>
                                    <td>30</td>
                                    <td class="font-bold">₹675,000</td>
                                    <td><span class="badge badge-warning">Low Stock</span></td>
                                    <td>
                                        <button class="text-blue-600 hover:text-blue-800 mr-3">
                                            <i class="fas fa-edit"></i>
                                        </button>
                                        <button class="text-red-600 hover:text-red-800">
                                            <i class="fas fa-trash"></i>
                                        </button>
                                    </td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
                
                <!-- Customers Tab -->
                <div id="dashboard-customers" class="tab-content hidden">
                    <div class="flex justify-between items-center mb-6">
                        <h3 class="text-2xl font-bold text-slate-900">Customer Management</h3>
                        <button class="px-4 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition flex items-center gap-2">
                            <i class="fas fa-user-plus"></i> Add Customer
                        </button>
                    </div>
                    
                    <div class="grid md:grid-cols-3 gap-6 mb-8">
                        <div class="dashboard-card">
                            <div class="flex items-center gap-4">
                                <div class="w-16 h-16 bg-blue-100 rounded-full flex items-center justify-center">
                                    <i class="fas fa-building text-blue-600 text-2xl"></i>
                                </div>
                                <div>
                                    <div class="text-sm text-slate-500">Total Customers</div>
                                    <div class="text-3xl font-bold mt-1">156</div>
                                </div>
                            </div>
                        </div>
                        <div class="dashboard-card">
                            <div class="flex items-center gap-4">
                                <div class="w-16 h-16 bg-green-100 rounded-full flex items-center justify-center">
                                    <i class="fas fa-star text-green-600 text-2xl"></i>
                                </div>
                                <div>
                                    <div class="text-sm text-slate-500">Active Customers</div>
                                    <div class="text-3xl font-bold mt-1">128</div>
                                </div>
                            </div>
                        </div>
                        <div class="dashboard-card">
                            <div class="flex items-center gap-4">
                                <div class="w-16 h-16 bg-purple-100 rounded-full flex items-center justify-center">
                                    <i class="fas fa-medal text-purple-600 text-2xl"></i>
                                </div>
                                <div>
                                    <div class="text-sm text-slate-500">Premium Clients</div>
                                    <div class="text-3xl font-bold mt-1">42</div>
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <div class="table-container">
                        <table class="w-full">
                            <thead>
                                <tr>
                                    <th>Customer</th>
                                    <th>Company</th>
                                    <th>Industry</th>
                                    <th>Total Orders</th>
                                    <th>Total Spent</th>
                                    <th>Last Order</th>
                                    <th>Status</th>
                                    <th>Actions</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr>
                                    <td class="font-medium">Rajesh Kumar</td>
                                    <td>Oil & Gas Corp</td>
                                    <td>Oil & Gas</td>
                                    <td>24</td>
                                    <td class="font-bold">₹2,450,000</td>
                                    <td>2024-03-15</td>
                                    <td><span class="badge badge-success">Active</span></td>
                                    <td>
                                        <button class="text-blue-600 hover:text-blue-800 mr-3">
                                            <i class="fas fa-eye"></i>
                                        </button>
                                        <button class="text-green-600 hover:text-green-800">
                                            <i class="fas fa-edit"></i>
                                        </button>
                                    </td>
                                </tr>
                                <tr>
                                    <td class="font-medium">Priya Sharma</td>
                                    <td>PowerGen Ltd</td>
                                    <td>Power Generation</td>
                                    <td>18</td>
                                    <td class="font-bold">₹1,875,000</td>
                                    <td>2024-03-14</td>
                                    <td><span class="badge badge-success">Active</span></td>
                                    <td>
                                        <button class="text-blue-600 hover:text-blue-800 mr-3">
                                            <i class="fas fa-eye"></i>
                                        </button>
                                        <button class="text-green-600 hover:text-green-800">
                                            <i class="fas fa-edit"></i>
                                        </button>
                                    </td>
                                </tr>
                                <tr>
                                    <td class="font-medium">Amit Patel</td>
                                    <td>Marine Solutions</td>
                                    <td>Marine & Offshore</td>
                                    <td>12</td>
                                    <td class="font-bold">₹923,000</td>
                                    <td>2024-03-13</td>
                                    <td><span class="badge badge-success">Active</span></td>
                                    <td>
                                        <button class="text-blue-600 hover:text-blue-800 mr-3">
                                            <i class="fas fa-eye"></i>
                                        </button>
                                        <button class="text-green-600 hover:text-green-800">
                                            <i class="fas fa-edit"></i>
                                        </button>
                                    </td>
                                </tr>
                                <tr>
                                    <td class="font-medium">Suresh Nair</td>
                                    <td>Chemical Process</td>
                                    <td>Chemical</td>
                                    <td>8</td>
                                    <td class="font-bold">₹1,580,000</td>
                                    <td>2024-02-28</td>
                                    <td><span class="badge badge-warning">Inactive</span></td>
                                    <td>
                                        <button class="text-blue-600 hover:text-blue-800 mr-3">
                                            <i class="fas fa-eye"></i>
                                        </button>
                                        <button class="text-green-600 hover:text-green-800">
                                            <i class="fas fa-edit"></i>
                                        </button>
                                    </td>
                                </tr>
                                <tr>
                                    <td class="font-medium">Meena Reddy</td>
                                    <td>Construction Co</td>
                                    <td>Construction</td>
                                    <td>15</td>
                                    <td class="font-bold">₹1,564,000</td>
                                    <td>2024-03-10</td>
                                    <td><span class="badge badge-success">Active</span></td>
                                    <td>
                                        <button class="text-blue-600 hover:text-blue-800 mr-3">
                                            <i class="fas fa-eye"></i>
                                        </button>
                                        <button class="text-green-600 hover:text-green-800">
                                            <i class="fas fa-edit"></i>
                                        </button>
                                    </td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
                
                <!-- Analytics Tab -->
                <div id="dashboard-analytics" class="tab-content hidden">
                    <div class="mb-6">
                        <h3 class="text-2xl font-bold text-slate-900">Business Analytics</h3>
                        <p class="text-slate-600 mt-2">Detailed insights and performance metrics</p>
                    </div>
                    
                    <div class="grid lg:grid-cols-2 gap-8 mb-8">
                        <div class="dashboard-card">
                            <h4 class="font-bold text-lg text-slate-900 mb-4">Revenue by Product Category</h4>
                            <div class="h-64">
                                <canvas id="categoryChart"></canvas>
                            </div>
                        </div>
                        <div class="dashboard-card">
                            <h4 class="font-bold text-lg text-slate-900 mb-4">Monthly Performance</h4>
                            <div class="h-64">
                                <canvas id="performanceChart"></canvas>
                            </div>
                        </div>
                    </div>
                    
                    <div class="grid md:grid-cols-3 gap-6">
                        <div class="dashboard-card">
                            <h4 class="font-bold text-lg text-slate-900 mb-4">Order Conversion Rate</h4>
                            <div class="text-center py-8">
                                <div class="relative inline-block">
                                    <canvas id="conversionChart" width="200" height="200"></canvas>
                                    <div class="absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 text-center">
                                        <div class="text-3xl font-bold text-blue-600">68%</div>
                                        <div class="text-sm text-slate-500">Conversion</div>
                                    </div>
                                </div>
                            </div>
                        </div>
                        
                        <div class="dashboard-card">
                            <h4 class="font-bold text-lg text-slate-900 mb-4">Top Performing Industries</h4>
                            <div class="space-y-4">
                                <div>
                                    <div class="flex justify-between mb-1">
                                        <span>Oil & Gas</span>
                                        <span class="font-medium">42%</span>
                                    </div>
                                    <div class="progress-bar">
                                        <div class="progress-fill" style="width: 42%"></div>
                                    </div>
                                </div>
                                <div>
                                    <div class="flex justify-between mb-1">
                                        <span>Power Generation</span>
                                        <span class="font-medium">28%</span>
                                    </div>
                                    <div class="progress-bar">
                                        <div class="progress-fill" style="width: 28%"></div>
                                    </div>
                                </div>
                                <div>
                                    <div class="flex justify-between mb-1">
                                        <span>Chemical</span>
                                        <span class="font-medium">18%</span>
                                    </div>
                                    <div class="progress-bar">
                                        <div class="progress-fill" style="width: 18%"></div>
                                    </div>
                                </div>
                                <div>
                                    <div class="flex justify-between mb-1">
                                        <span>Marine</span>
                                        <span class="font-medium">12%</span>
                                    </div>
                                    <div class="progress-bar">
                                        <div class="progress-fill" style="width: 12%"></div>
                                    </div>
                                </div>
                            </div>
                        </div>
                        
                        <div class="dashboard-card">
                            <h4 class="font-bold text-lg text-slate-900 mb-4">Customer Retention</h4>
                            <div class="text-center py-8">
                                <div class="text-5xl font-bold text-green-600 mb-2">92%</div>
                                <div class="text-slate-600">Retention Rate</div>
                                <div class="text-sm text-slate-500 mt-4">Industry Average: 85%</div>
                            </div>
                        </div>
                    </div>
                </div>
                
                <!-- Settings Tab -->
                <div id="dashboard-settings" class="tab-content hidden">
                    <div class="mb-6">
                        <h3 class="text-2xl font-bold text-slate-900">Account Settings</h3>
                        <p class="text-slate-600 mt-2">Manage your supplier account preferences</p>
                    </div>
                    
                    <div class="grid lg:grid-cols-2 gap-8">
                        <div class="dashboard-card">
                            <h4 class="font-bold text-lg text-slate-900 mb-4">Company Information</h4>
                            <form class="space-y-4">
                                <div>
                                    <label class="block text-sm font-medium text-slate-700 mb-2">Company Name</label>
                                    <input type="text" value="Ultimate Flange Manufacturing" class="w-full px-4 py-2 rounded-lg border border-slate-300 focus:ring-2 focus:ring-blue-500 focus:border-blue-500 outline-none">
                                </div>
                                <div>
                                    <label class="block text-sm font-medium text-slate-700 mb-2">Contact Email</label>
                                    <input type="email" value="supplier@ultimateflange.com" class="w-full px-4 py-2 rounded-lg border border-slate-300 focus:ring-2 focus:ring-blue-500 focus:border-blue-500 outline-none">
                                </div>
                                <div>
                                    <label class="block text-sm font-medium text-slate-700 mb-2">Phone Number</label>
                                    <input type="tel" value="+91 7307709671" class="w-full px-4 py-2 rounded-lg border border-slate-300 focus:ring-2 focus:ring-blue-500 focus:border-blue-500 outline-none">
                                </div>
                                <button type="button" class="w-full py-3 bg-blue-600 text-white rounded-lg font-medium hover:bg-blue-700 transition">
                                    Update Information
                                </button>
                            </form>
                        </div>
                        
                        <div class="dashboard-card">
                            <h4 class="font-bold text-lg text-slate-900 mb-4">Notification Preferences</h4>
                            <div class="space-y-3">
                                <label class="flex items-center justify-between p-3 bg-slate-50 rounded-lg">
                                    <div>
                                        <div class="font-medium">New Order Notifications</div>
                                        <div class="text-sm text-slate-500">Get notified for new orders</div>
                                    </div>
                                    <input type="checkbox" checked class="w-6 h-6 text-blue-600 rounded">
                                </label>
                                <label class="flex items-center justify-between p-3 bg-slate-50 rounded-lg">
                                    <div>
                                        <div class="font-medium">Low Stock Alerts</div>
                                        <div class="text-sm text-slate-500">Receive low inventory alerts</div>
                                    </div>
                                    <input type="checkbox" checked class="w-6 h-6 text-blue-600 rounded">
                                </label>
                                <label class="flex items-center justify-between p-3 bg-slate-50 rounded-lg">
                                    <div>
                                        <div class="font-medium">Payment Notifications</div>
                                        <div class="text-sm text-slate-500">Get payment status updates</div>
                                    </div>
                                    <input type="checkbox" class="w-6 h-6 text-blue-600 rounded">
                                </label>
                                <label class="flex items-center justify-between p-3 bg-slate-50 rounded-lg">
                                    <div>
                                        <div class="font-medium">Monthly Reports</div>
                                        <div class="text-sm text-slate-500">Receive monthly sales reports</div>
                                    </div>
                                    <input type="checkbox" checked class="w-6 h-6 text-blue-600 rounded">
                                </label>
                            </div>
                        </div>
                    </div>
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
                <div class="space-y-2">
                    <!-- Dashboard button will be added dynamically for suppliers only -->
                    <button onclick="logout()" class="w-full text-left text-slate-500 hover:text-red-600 font-medium py-2 flex items-center gap-2">
                        <i class="fas fa-sign-out-alt"></i>
                        Logout
                    </button>
                </div>
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
                            <!-- Dashboard button will be added dynamically for suppliers only -->
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
                            <!-- Hero Image Container -->
                            <div class="hero-image-container">
                                <img src="data:image/jpeg;base64,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" alt="Industrial Flange Manufacturing Facility" />
                            </div>
                        </div>
                    </div>
                </div>

                <!-- What Are Flanges Section -->
                <div class="mt-20 pt-16 border-t border-slate-200 reveal">
                    <div class="text-center mb-12">
                        <h2 class="text-4xl font-bold text-slate-900 mb-4">Understanding Flanges</h2>
                        <p class="text-slate-600 max-w-3xl mx-auto text-lg">Essential components in industrial piping systems that ensure secure connections and operational reliability</p>
                    </div>
                    
                    <div class="grid lg:grid-cols-2 gap-8 items-start">
                        <div class="bg-white p-8 rounded-3xl border border-slate-200 shadow-lg">
                            <div class="flex items-start gap-4 mb-6">
                                <div class="w-14 h-14 bg-blue-100 rounded-2xl flex items-center justify-center flex-shrink-0">
                                    <i class="fas fa-link text-blue-600 text-2xl"></i>
                                </div>
                                <div>
                                    <h3 class="text-2xl font-bold text-slate-900 mb-3">What Are Flanges?</h3>
                                    <p class="text-slate-600 leading-relaxed">
                                        Flanges are widely used in numerous applications across engineering and industries as they play vital roles as linkages between pipes, valves, pumps, and others. They offer an opportunity to connect or link various elements of a system in a way that is mechanically possible. Generally, flanges are anhedral circular plates with holes arranged uniformly along their circumference for bolts or studs that join them.
                                    </p>
                                </div>
                            </div>
                            
                            <div class="bg-blue-50 rounded-2xl p-6">
                                <h4 class="font-bold text-blue-800 mb-3 flex items-center gap-2">
                                    <i class="fas fa-cogs"></i>Primary Functions
                                </h4>
                                <ul class="space-y-2 text-blue-700">
                                    <li class="flex items-start gap-2"><i class="fas fa-check-circle text-green-500 mt-1"></i>Secure connection between pipeline components</li>
                                    <li class="flex items-start gap-2"><i class="fas fa-check-circle text-green-500 mt-1"></i>Easy assembly and disassembly for maintenance</li>
                                    <li class="flex items-start gap-2"><i class="fas fa-check-circle text-green-500 mt-1"></i>Pressure containment and leak prevention</li>
                                    <li class="flex items-start gap-2"><i class="fas fa-check-circle text-green-500 mt-1"></i>System flexibility and expansion capability</li>
                                </ul>
                            </div>
                        </div>
                        
                        <div class="bg-white p-8 rounded-3xl border border-slate-200 shadow-lg">
                            <div class="flex items-start gap-4 mb-6">
                                <div class="w-14 h-14 bg-green-100 rounded-2xl flex items-center justify-center flex-shrink-0">
                                    <i class="fas fa-industry text-green-600 text-2xl"></i>
                                </div>
                                <div>
                                    <h3 class="text-2xl font-bold text-slate-900 mb-3">Our Manufacturing Capabilities</h3>
                                    <p class="text-slate-600 leading-relaxed">
                                        We specialize in precision manufacturing of industrial components with comprehensive material options and rapid production capabilities.
                                    </p>
                                </div>
                            </div>
                            
                            <div class="space-y-6">
                                <div>
                                    <h4 class="font-bold text-slate-800 mb-3 text-lg">Flanges We Manufacture</h4>
                                    <div class="grid grid-cols-2 gap-3">
                                        <div class="bg-slate-50 p-3 rounded-xl">
                                            <div class="flex items-center gap-2">
                                                <i class="fas fa-circle text-blue-500 text-xs"></i>
                                                <span class="font-medium">MS Plate Flange</span>
                                            </div>
                                        </div>
                                        <div class="bg-slate-50 p-3 rounded-xl">
                                            <div class="flex items-center gap-2">
                                                <i class="fas fa-circle text-blue-500 text-xs"></i>
                                                <span class="font-medium">Forged Flange</span>
                                            </div>
                                        </div>
                                        <div class="bg-slate-50 p-3 rounded-xl">
                                            <div class="flex items-center gap-2">
                                                <i class="fas fa-circle text-blue-500 text-xs"></i>
                                                <span class="font-medium">Weld Neck Flanges</span>
                                            </div>
                                        </div>
                                        <div class="bg-slate-50 p-3 rounded-xl">
                                            <div class="flex items-center gap-2">
                                                <i class="fas fa-circle text-blue-500 text-xs"></i>
                                                <span class="font-medium">Special/Ring as per drawing</span>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                                
                                <div>
                                    <h4 class="font-bold text-slate-800 mb-3 text-lg">Additional Products</h4>
                                    <div class="grid grid-cols-2 gap-3">
                                        <div class="bg-slate-50 p-3 rounded-xl">
                                            <div class="flex items-center gap-2">
                                                <i class="fas fa-circle text-green-500 text-xs"></i>
                                                <span class="font-medium">Pipes Fitting (B/W & S/W)</span>
                                            </div>
                                            <p class="text-xs text-slate-500 mt-1 pl-4">Elbow, Bend, Tee, Reducer, Cap, Coupling, Union</p>
                                        </div>
                                        <div class="bg-slate-50 p-3 rounded-xl">
                                            <div class="flex items-center gap-2">
                                                <i class="fas fa-circle text-green-500 text-xs"></i>
                                                <span class="font-medium">Pipes</span>
                                            </div>
                                            <p class="text-xs text-slate-500 mt-1 pl-4">Round & Square Pipes</p>
                                        </div>
                                    </div>
                                </div>
                                
                                <div class="bg-gradient-to-r from-blue-50 to-green-50 rounded-2xl p-5">
                                    <h4 class="font-bold text-slate-800 mb-2 flex items-center gap-2">
                                        <i class="fas fa-boxes"></i>Material Inventory
                                    </h4>
                                    <p class="text-slate-600 text-sm">
                                        Our comprehensive inventory includes stainless steel, mild steel, alloy steel, and other unique materials, allowing us to commence production immediately upon receiving your order. We hold a wide stock range of austenitic 300 series, mild, alloy, and other unique stainless steel qualities, and we can begin fabrication immediately after placing the order.
                                    </p>
                                </div>
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
                        <span class="text-blue-600 font-bold uppercase tracking-widest text-sm">Product Catalog</span>
                        <h2 class="text-4xl font-bold text-slate-900 mt-2 mb-4">Explore Our Products</h2>
                        <p class="text-slate-600 text-lg">Browse our extensive range of industrial flanges and precision components</p>
                    </div>
                    
                    <!-- Product Thumbnails Grid -->
                    <div class="w-full grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6 mb-12 reveal stagger-delay-1">
                        <!-- Weld Neck Flange -->
                        <div class="product-thumbnail" onclick="updateProduct('wnf')">
                            <img src="data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAkGBxISEhUSEhMWFhUXFxgVFxcVFx0YFxcYHRcXFx0YFxYdHSggHR0lHRcaITEhJSkrLi4uFx8zODMtNygtLisBCgoKDg0OFxAQFy0dHR0tLS0tKy0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLf/AABEIALgBEgMBIgACEQEDEQH/xAAcAAACAgMBAQAAAAAAAAAAAAADBAAFAgYHAQj/xABDEAACAQICBwUFBgQFAgcAAAABAgADEQQhBRIxQVFhcQYTgZGhIjKxwfAHI1Ji0eEUQnKCFSRDU/Ez4hZjc4OSwtL/xAAYAQEBAQEBAAAAAAAAAAAAAAABAAIDBP/EAB4RAQEBAQADAQEBAQAAAAAAAAABEQISITFBUWET/9oADAMBAAIRAxEAPwDSFhqcCsKk9bzDpGKZiyRinAmUjNOKoYzTMkapxqkYpTjNIzLUOUzGqZidI/X19ZxqmYNGkjFMxZDGEMiOkPTi6wyGBMLMxBIY9g9H1KmYFl/Ech4cYEC88Zhv+vq02HD6Fpr713PPIeX6x+lQRfdUDoAJnyONOYcj5EwTPN6njKDkRfrLyWNCYwTTdMToeg+1ADxX2T6bfGUmkOzlRbmkdcfhOTeB2H0jOoMUDQDwznMgggjIgixHUHMRd5tkN4tVMPUi7yBeoYtUjFQxapEUCpF3MO8XcxZL1ItUMPUizxALxd4d4BzJMJJjrSRCKYVDAqYVDJGEMOhiyGHQwJlDGKZiqRimZI5TMapmJ0zGaZhTDlMxpInTMaTdMtm6ZjCGK0zD0zJGUMOkWQzY9EYHUAdx7RFwPwjieeXrCtSaa0RoYD26oudy7h/VxPKXoi1B4zOdbSSSSCSVfafTtLA4apiavupawG1mJCqo6kiWk0P7aNF1a+jj3YJ7uotVlG0qAQT4Xv0BknO1+0/SVasGWoEBIC0kQMu3IZgsfMTtnZrST4jDpUqpqVNjqDcAjeMzkdtt15wL7L8EDXdzmyoNUc2axIHQW8Z9AaBwhpUgGFmJ1iOF9g8o56DzTGhqeIHtey491194cjxHIzQ9IYSrQfUrKBcnVdfcfpwP5Tn12zp0V0ngKdem1KoLq3mDuIO4jjKXFZrmFQxZzJig+Hrtha/vrmj7qibQevETx51jnYBUMVqRiqYs8WaA5i1QxioYrUMQDUMWcw9QxaoYgFjAOYVzAOYoMmeSXkkGSwiwKwqyQ6GGQxdIdIEzTMYSLIYemZI5TMZpmJ0zGqZgTdMxqmfrzidM/X19ZxmmYNHKZjCGKIYZqoVSxNgoJJ5DOBW2jANbWbYNgOwncPrlL2nir7ef16zmuA7SK+dwBzl//jgXVUBndslRBdm6DhzOUy3PTeqFa311jtPEC1ychtuch4/Wycux/a5KB/zOKSib/wDRoKa9Xo7r7KnxhMN9qWiyNSouIdd5emHB56tzM3Gtb9X7S4dTZWLn/wAsFvWAPahP9qp4iLaG0ho/HL/lai7PdF0cf+2wBHW0T0vo+pRuynWX1lJBdXdHtLQO0lf6hLWjXRxdWDDkbzkekNOovvbeG+V2D7Q1UbWosV5X9kyvMU12LCaEw1JzVp0KaOdrKgDeYHKPzWOyfaxcV7DjVqDduPSbPMlJJJJJp32mdn/4nDGrTH31AF0I2lRmV9LjpOdaI0iKyZ++uTc+fjO41KotOCdqMJ/AaRfVypOdYcNRjs/ta/lzmubgs2LGqYu5hnaLvOrjQXMWqGGcxeoZoAVTFnhqhi7mQCqGLuYZzAOYhhJJJJPRCKYEQqyQyQ6GLrDJAmUMOhiyGHpmSN0zGaZilMximYE5TMZQxRDGKZg1DiGUvbXH93htUbah1PDafQW8ZboZo/2hYq9WnT/ChbxY/wDbM9fGufqppYU1aiUgL5A23Zi9z5+ktNK6e7tDhsK1hbVq1h79T8itupjgNtokMSVohtjle7Ujbq7SfAMB48pTqs5ujJKK9YwhAggDIBArHC45kYMrFWBuGU2IPIjfO5dj9LV8TQFPGKBVsQjHI1F4Ou5vjy3867CaAFhiaouT/wBNTsA/GRx226Xm8B7WIyN7g8Oc3IxelD2r7IFaoYNkdl8yN2q3TjvEywOgEQXZr5Sw7T4tmAe59sX6MNtuF738ZoGle07qurfPZH1F7rcP/ENLBOTSUFthvvE3vsj2wp4xQMg/CfNdTSDMSSTLPsrptqFYEGwuJndax9SPWA+usXrYvdNdwemxUpq43gHbv3+s9bHZ3vLxWxaV8TOdfavhBUpU6wtdGKH+ltnqPWbJWxkou01XvMNWS/8AISOoNx8JrB5NU0Li+8oqTtHsnqP2tGKhlF2Yq51E6MPh+kuqhmufjl19BqGLVDD1DFahm2AXMXcwzmLuZIJzANCuYBjEMbyTG8kiIsIsCsKsgMsMhi6mGQyJhIemYusPTgjNMxlDFUMYpmSNUzGUMUpmHQzLUOI0512sbXxrrwKIP/ip+JM6ChnO9Nn/ADz/APqL8FmO/jpwDpOuCQBsAA+J+fpFVcReoMzMZzdDhqDjD6Nod7VSmP5mC+ZzlZLrsYt8dQ/qY+VNz8ZQV1+kgVQoFgAAANwGVpleYa08LTs5k9Nt93b81x12fD4TlvaLDkVDYZbfOdF7U1dWkpv/AKijzvNcpYcVcQq31gRbZ+UmY6jfN9NEmVM2IPMTf9IdiQRdcjNdr9l66uFCls92czlOtw7OaZK0tUnYfQiXH+M85zDG4pqNRqYOzI9bT06Ue23eY+Q8Y6VV0tzimIx9wbnaCPSaCmk3N8/rznr6UfZePkvGHNBPbEleKEfA/KbG5ms6MFsUBv1L26p+82NzN8fHPv6C5i1QwzmLOZtzCcxdzDOYu5kgnMC5hHgXMQwMkxLfX0Z7IiLCLBLCKZAZYVDArCqZIwsOkWQw6QJpDD0zFUMOhkjaGHUxVDDoYE2jTQO1C6mNZtxKN4aqj/6mb0jTVO2uG+8pvxWx8Df5zHc9OnF9te0lS1ajDx+vG8Vl7jMGatAVhtp2R+hsAfPL+6VHcTk6hot5a6AqCliKVTcHF+hy+Blb3JmSqZB2zWk1pr/ZXS/f0QGP3iCzDiNzeMuy07OTXu3AaolOih9pmLeCjM+bDzmlYYVkq2FQhlBzG7K1pumPxgD1Kze6i6i+GbEdTYf2zRaeMzZiMySfW/xnPr66c/Fo+kcYP9cnxhMBp/SCVNanVzUHaFOViDulNUx8PoirrsVt72Vxtt9CGlW4yu9R2eobuxJY7M5ijR3HYKzNbjFmokbYFgHnjVOE9KTyjRLMFH19Wkm0YAo+MqsmahdVTfIgBUy62JlxUMpOyuH1VdzvIXyz+cuHM78fHDv6C5gKhhKhgKhmmAXMC5hKkA5ig2MC8I5gXkA5JJJEVTCCCWEWSGSFEAsMsgOkMhi6GGQwJmmYdDFlMw0AO+VmqEkjYASo2HhaZtxrnnVmhh1MoKtd1VyrMADkt7jdvOfrGNBY96obWt7NgLC3GE61q8ZF6piHaHDd5RvvQhvDYfT4RxTCbRbdGzWZca1oPEd02a6yMCrqdjAixB6g+sFpjQvckOh1qL+452/0PwYeu0SyGF1WK/Vt0bod5TDamqwbJ6bi6VBzG48+U5Y7tXTDg7vhIcFfdLutQwrH3qmGf8LjXT+1wb28zBjBNewr0X4WLX9VEMRHAUalJw6XDDfuI4HiJtuG0g1ZLKpVtjHcOJHPlFKGjABrVHW2+2XqZ5jdLqq93Qyy97hzXnzmp6F9qPtTiAD3KbB73XcJrjJyl1XpKf3ihwhJsmZ4QSqNM3sN82XQOj2pqajixI9kGP6C0AB97WGzYJYYxNY5CwGwSwxq2NfVNht38pajQetSDX9ojWtbLw5yl7RYVhUvb2SPUbfGbHgNJju1FnZgACEQvsy3CXOfrPW/jWa+BJ93bwkwmHZFdmBGWoL8W228L+cdx66zn2aq3Nx9028wy09QprszWN8qb+H8sMaWWCo93TVeVz1OZmTGYjFKx1b57bHI+RmLtO8ee/6G5i7mFqGAcxAbmAcwrmAeIDaBYwjmBeRYyTySSZhxxhFqDjFAsyCw2nIcWqOMKtZeIiAEzFMxCxWuv4hCriE/EJWrRhVoyR6vjVVGIYEgZdZuX2X6HpNhGqVV1ida1yeg2HnObaTFgF4mdm7E0u7wI/pP16Tl1drrxMjm/aJAneqgsBUANuBW/wARE+zmICsynIHPxjWl21jiuT0z4feD9JR0X1XB5CY3K3ZsbmuLT8Q84VcXT/GvnKtMOCARsOcKuFnZwM42ultYMLjhwg1xF/2ni4SAfClD+U+nKY6n66cdfhHSmm+7bUCBjle5y6bNucewlGniKYdfu24qcwefGUWmtG1Lmrf7skC98lNgLNwvuvLvsnSKoRcFb5EeN/rnMR0KYzReIGZcuBxz+MXp0X3m3UWm2Yhha15U1qYkgMNo0N7zjpsMu8JhqVL3RrGU9KhYy5oU8hGJm9Qsc/IbBPe6mQSM0luI4LWt9p0tSBH41+ctewtJdS9he5zlJ2xr5pTHNz8B850n7HtEUzhS9RAxJJFxeZ+VX3Gg9qHIrXB2G4+vOE0Eoqm9T2jfp8JY/a9Sp0sUopqFva4XZuvAYajqU1ZBbIGM+r8Vna5FXEUdUAAHO2WXOLPik/EPOXXbLC6+AWtYF6dUEtbMqcrE7bXmqd1cAjYReb4/XLv8ONik/EPOBauv4h5xVqEC1GdGDTVl4iCaqOIixpzDVghmqDjBs4gysxKw2nIJrjiJ5MNSSW05BwkzWlDKkKqTTIS04dMPCd2bXAv0225RWrZ9rEcr6vp4zn13np05433VhSwmV7G3IfOEWmvKViYFdliRzJj1DDWGqBYWH6/XWY8q6TmfxT1GFXEADYCALcjO2YAamEt+T5XnJ8Bhu6qh1Njt2AjyN5u+N7UV6VHMd4NmqlFTu2mwyHOUValiFu+JHEKfIygrps5Ej5/OWGO0satTWamyXFiEAQ+PsxehW9r2QwG7WtfzFvhMlbYHWCDWUjh0ntXGVFNlpMRx1gB5TOjWFrsc+ZkfEqOJ8D84pnR0hW1gO7sN5LA+m2W+j6y1SUK5gXPAjZ8xNcq6QP8AKo/uPyEs+xbs+JYtt7s7Ba3tLGVmyG8Vo56dyt2S2dtoG8HiIKjVsBbZNm0lXakt1Qt0mn43St2v3JU77ZX+Ubz/ABTv+mqhJ/aDWgZ5hdI0W2nUP5tnnLSnqHNWB6EGGNbClHDfX14yyoplBl1UXJAA3mKtpmmPdz9BGC1Yakxp4gK1ife2dYimk78B6yr03jKwBZVpFF9r2r62XLZfpLRIptOV9evVIzAbUHRcj6md7+zGhqYRRyE+d6NyVG8sL+JufjPpjsTT1cMvh8JhpyD7ZKt8XfgQPQQ+hiHojpKb7VKt8W5/NLHspWvTX65zU+i/F/Wwfe4KvT4oSOoFx8JznQp1qVjtU6v6Trmh6XskHmJxw1jhq9amRkGO3kf0Mdy6zmxYvSgHpTxdMUyLmw87+VvnDDEo381uv67JudRzvFKNSgHpSydIu6TbKvanMLR11gXSSAtPJnqSQR9VhkWYqIZRFDYY5MOnzhSFbaB4iKPRJsymxEySuw95L81/Scuufbrx1Mxa0EsMtU9VU/ERmnVFwClM8fYAtlylZSxq7ww/tv6iNLpKnvY+IP6TOV02Ga1VR/oU7326h557eUwOOe1gFHRbfGAqaRpfjHr+kVq42n+L0P6S9r0zr0w+bAE7dlvhPKVJRkFUeAHrFH0hTHE9FPzmB0qNyOfACGVbFidnPLdsyiFdszlfqYu+NrNktMDrc/pBfwuJfbcdMvhHxrN6jHEVgNpt02+UvuwWJXvmy9oqQOQuD8pV4bsy596bZ2a0OtFr77fpGc4L1rbdUTBsBTbagPhIjxmk9ogg/ZjDttQDwgW7G4bcCOhl4Ks97368ZHI5J22wpw9cUlJ1NUMCSTcn/iUCV26zpXbDBrVqWYfyix3jbsmj47s9VW+qNZeW3xEzWgaOI9rV1lBy951UcNrECD05SqAgOwsReyurg+KsQYN+z1cLrd1U1fxKNYDqRsngwqk3Iz+t0yTXZrCiviKa6yoL31m2Az6W0JgjRoBLhiBkQcj4z5jwmF9sdZ03RJYU/YrVF6MR8DGTRbjT/tL0TilxDNUouAWya1wfKTs3r0l+8BUfmylt2kxeIJBNd21SD7TE7Os1HTekXdyWVWN9pGe085fC6VozT2HS4aqu2+3iJoHb3R5WsMShDU6uYK8RtBG6UdDFG+SqPD9ZnjsbUNgbm2eZuvgtspW6JMY00VhfVHlCFbbJno/H0iCtWmxy95H1T5FSPhBrWVydW4Az9rb6TLSJWZdht9cI3QxgbI5H0MSanMRQcuECkNzFrDiZqdWM3mVaOsAyxpxAuJ6HnL6kkJJIGVhVMAphVMCYQwqmLqYRWkTSgQyKIqjwyPDFo3dCT+HWeLUmaNeB1BhU4QtPDLwmMzRpYdGSkvCHRRAq0ItSQ0yiRuh7MQWtMhXg1q2WqIZa0plxMy/iufz/AGktXgrz1sQBtMohjevnMhjBwli0DtDjqest2AOzPYepnlO2QlX2j0cK4BBlHhcVicN7J9tBubd0MsPl+VvuDqsrgqSpIPtKbHzEtK+kbi1WklfK/wB5TVj57Zp2j+09E5PemfzC48xNhwmJp1M0dWytkRv/AOJISvo/AN7RwgVuNOqy59DcQT4jDoLItUDmyt+kJWNpU1Rlblnz2/tDDLqv0wS/uq3K9v8A9SkxGhw+eswPAp8wTL4oc+dtvThMGGfh85ityNZGgGB238CPlM20LUY3y8T+0vDew43OXHPlCUqZ233/AKiWFSJ2ff8AEg8/0juE0BTGdRzzCgDLqSfhLRgcvWAamxvzB9ZAzhsSmHINFAr7mIDN1G4eUqsfiWZi7klmNySbk9TDYjKxvawlNiMchbVBvzGwS+q+keBaZu0ExnoeZhPZ5JICBoRWkkkWatCq0kkEIrwgaSSSEWpCJVnskkJ3kiVJ7JBCirM1qz2SRZirJ3skkky72ed7JJJPe8k7ySSSYtVg3IO0SSSRapg0O4RSpotNq3B5G0kkizQYhfdrv0Y63xvM/wCNxQ/mRuot8xJJDDtef4jW3op6G36wT6VcbaXk37SSQyNeVYf42f8AabzkOnj/ALJ8/wBpJJeMH/Sh1NP1f5aQHUkxSppbEnZZeg/WSSXjF5UjWSq/vsT1OXlsmVDC2zkkmpIzbTLGCYz2SaZgetJJJJP/2Q==" alt="Weld Neck Flange" />
                        </div>
                        
                        <!-- Long Weld Neck -->
                        <div class="product-thumbnail" onclick="updateProduct('lwn')">
                            <img src="data:image/jpeg;base64,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" alt="Long Weld Neck Flange" />
                        </div>
                        
                        <!-- Slip-On Flange -->
                        <div class="product-thumbnail" onclick="updateProduct('slipon')">
                            <img src="https://bfnf.in/public/image/f249688537eb6cd7c908424877322dfc.png" alt="Slip-On Flange" />
                        </div>
                        
                        <!-- Blind Flange -->
                        <div class="product-thumbnail" onclick="updateProduct('blind')">
                            <img src="https://bfnf.in/public/image/3ea4a78a91ab1bac509e181ff3c73f54.png" alt="Blind Flange" />
                        </div>
                        
                        <!-- Puddle Flange -->
                        <div class="product-thumbnail" onclick="updateProduct('puddle')">
                            <img src="data:image/jpeg;base64,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" alt="Puddle Flange" />
                        </div>
                        
                        <!-- Plasma CNC -->
                        <div class="product-thumbnail" onclick="updateProduct('plasma')">
                            <img src="data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAkGBxITEhUTExMWFhUXGBcXFxgYGBgaGBgYGBcXGBcYGBgeHSggGBolHRgYIjEjJSkrLi4uFyAzODMtNygtLisBCgoKDg0OGhAQGi0fHyUtLS0tLS0tLS0tLS0tLSstLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLSstLS0tLf/AABEIANYA6wMBIgACEQEDEQH/xAAcAAABBQEBAQAAAAAAAAAAAAADAQIEBQYHAAj/xABIEAACAQIEAggDBQUFBQgDAAABAhEAAwQSITFBUQUGEyJhcYGRMqGxQlLB0fAUI2KC4QdykrLxM0OiwtIVFiREVGOD4pOz0//EABoBAAMBAQEBAAAAAAAAAAAAAAABAgMEBQb/xAAtEQACAgEEAQIEBgMBAAAAAAAAAQIRAwQSITFBIlEFE2GRMkJScYGhseHwFf/aAAwDAQACEQMRAD8A5rccfeFQVP7xY51pTav8UsH0blFVN/B3e0DNbGYggZAY0Gs8jB/CsoyTPRy6LLj9Vf0yy6GuxdGkyCI5zWnvWGAAjifwrIYOzc0cI3rofYmRVrf6zFWVIYOIkEKB4d4mKxnG3we1pdUseL18fuW6WSeFYbtHG7H3rR2+sJuSBuDG67+GuvpTOkuhwlhL/aORcbLlIAIP2uJ0Hz8NqeOL8o5fiOp3RjOEvszK4m43OndH2nuBUQZmJIAEanXTWr3rL1ZNjC2sR2pc3UFxVFtiAJUMHcDKpE8d4oPVrDrbz3mGZbZhQwIzMeYOwj8a2pUeT8+bfLssrds2kt2kGa6RIA2Wd3PuQJ86tkwwsWXJ77ELmPOGWAJ4Cs5gukwS7FwHaSSSATGo8ttqlX+kmdAuaRtv+NZSvo9PBBRi8sncq4+gl25bd5IhMhMRxJAJ0oBWwNVbKeYJHj+XtVhgeiXvdoihu1S13bYSWZ+01TWCDUHFdW8cvxYPED/4Xj3intvyc2PWbW3KClbsq+lRnkm4WJ0ktJI03PHYVAwVrvfrwp/SFl0JV0ZSDEEEEHkRuDXujhETVpUiZZYZcsWo7ToPVOBYaT9ox7D8Jqv6UsY1GZrFy9lJkBXLROpGUiBUjoK5lw7knYz57Uyx0jd1i4OMA5SBWcLt0d2teNQip3/B7B9P9LWtQzkZgIe1mMeelWnSPXe+ytav2MJdm0Stzs2DoWAC6NswJB9KjL0nf/gbzH5RVN1i6RZ4VgARq0TG2g19/atHZ58VgXKk7/72If7XetgvZXK3ZtLAkFUIysZkZTHEcTUnqrj7oUrZTO4ZcilgoLFtACRG/OKjdB9PrYvF2s9pmtvbABGhcABoIMxFTepYyOg5Oh9iDUyfp5OnTK89Qlarv7+53HBdI9HXQLN65hjeWZt3Gt5xqSAVJk6EcONcz69dRry3buIt2z+zA5lKXFKoumgTNoJnQCK0t7pPAXVyXjeDrJbKWy6EsYWSp0H3eNchx+Et27twWrjFGJgRkmdtFAA34AVpfpOXHFrLKqffD/cndXgVYAkk5xvy1J+ZrrnRty4uGLi0rJEhs4DaASCrACJH3uNci6s4YqwDGWEkzrqdB8if+HjIrTdJft4tP2Rs3bHxGzcWSsKMxDAhtYmJ41mn6zo2btPwvP8ARtcD0Q2HvM5YsrFXzqmWCRBAkkEiJ/CrnqvjlN/EPJi4wILCIylwddRvybidBx5n1GuItp3fPa1uOwXXLbCEhLcyWaRAkbtGtdP6n9DvZVc926XdVLLK5EY5mdR3QYk8ddKqCfRw5+H34NDi7rAgKobjq0fga4L/AGjdOftONeAAtodiIMzkLZjMCe8W9BXWOvnWY4HDXrwQswK27eoC53Ayk6zAknbhXzNcxBjLJJO5Op8T5mt8a9VnJLqiwtXczZuGw8uJr6V6t4m9iMLYvZ0l7ak9w/FEN9rmDXzRhLojYj00r6C/s3xlwdHWAEBA7QTmI2u3OGU1eVWiYdnIxZvZc/YXMuYrP7v4huPjpr9ou9m4NM2y/Dz+KtPhs37K4b4luIx/nSD5a1RYbGMr9leZSe92bgrlcGRlIGiuJiK5fkxPZ/8AZ1Hsvt/sjh7mn7m7qJGg1B/mqk61Ydg1vtLbWyVMZxEieEHz/Rrc9G95bKkwcuQ78NNY14VT/wBoKArZbOGK9yAzK47usgjK2oEkHl4y1CMWTl1uo1GFpxVeWl0ZPot0TMDBBj4e8ePtUu6zfCIK7eOpJAJ8JMeZFH6tW81whgxGQnVViQR9rerzFdG5iCsDz02pN1I2wYZZtJVXT/k3v9ntxL3R9u3cCuhDIyOAykB2EFToRoN6z/TeH7fHYoqABas33WAI7RLXZWz5ggGs1hkbDWyHvZTmJUIbhBEkmYXQ6/Wtd1YuK14IRJu4e9Mic372J8TA18xzpbrZx5tLLDCMpPl+K5Rxa7iGdbY4IGyxv3mLEk85NbTorGNc6Mt2smbsMSWbKCWyXFuXHLiDIi22xGwnjOHwgkfrlWk6sYwo7KWOW4lxGWZBBtOJZPi0DNqDx30rajhs2PVTFdljrF9rgi72jXJ1KhbmpeRpMSIn612m5i1uW1dGDK0EEcRrXA8PhxffDoYtW8iLdug/CrdmXYljlB+OCBxk6DTrLIjYI2sDdCx3bb520IcMxzwS094zrM8jWL4Zp2jk/wDaTftt0heR8N2hR0IYXCrNmS25UhVOh25xsRWdPQrLdVXVsMpJEuWuZY1+FUkxIHl71u+urdliA5uk3WRYEKwzpbtqcpgGJ1kgxM6VW9XusWZv2e5hrTBm1LkLGgO50I0kbb1olwW5tdoqOoWKsNjDaxhd8ORcChUuSzgjJ3bUvsG0E+NdU6MToO+WsYe3YdpGZexYGQY1LpodNdd99TXIeq8DESIlQxXfQ7TvroTuK1vQY7K7nGpIIM8ZJJn1j2qZUjswYcmeLk5ceDRdb+h8GtxMLZw9mxFp8Vib62kz2sPb0At6aXHbug8IOhrlWKtotsGZfiDJjidePHjOtdC6MvW7mLujEMvZ3Ww4dn07lkPeyiODXDbBHImud9OXLTYm8LK5LFu4yIMzPnVGK5yzy0tBPgCPM3GNnDkTxyqRO64dXewbtEZFXKgyicwbKMxJJ3JPDgducboHFFcTh1Pwvcthm17oZwpMeAM1O6dS1jS+JU2LBAzPnuHMZZUUEhPEVX2ejbtjEWluFWJKsuSTpmIA1UGdDwpNccl4ZzjL0Ovqa/ofpcdpdS9dcJlTIAqfaa5MysxAFR+muibFy5OFYhgoLPcMgksBCKqwGC5jPONNZqqw+Bv52m0wkLqdtMxOv8wrQ4CyQuYkd7aOA21030rGWSnwetpvh8MsVKUnbu0Yp1vYQjMJkwCDMnc7iaPd6SxTM0QA3nt7x8oqy60Wwz2V5vP+UfjRLtoKJ8h6kwPmaW7izV6JOcsbfpjX+LNH1NWx+5e86ItrvOHcfvLwM22VTrkXusf4iu2U11HoXpKyQAt1WICnunN3WBCtpwOV4PHKeVcRXDFgAIkcyBvvqSAOFa/qtfuWLFzNiMN2rMoRbl1RltKrgCRpINxiJJqoM8/W6TJGfCbsrv7ausaXV/YrTd5Lq3LummzhVngRKEiOI10g8nFlV1DSfPX0rWP1Lvu9x7uMwuZy7yMSHOYkmWJgd7znXzqn6e6AvYZAzXLF3UhjbuhwBAI00bnuP69UXFHC8GV/lf2ZCwzMWCgySYAjWToAOMkxX031YVcPhLFkhgyW1DwjkZyJfXLr3ia+dOoWOC46w7LpbYvpO6o5XTkWCj1rsvR3XMrbUXXzPEsSrHVu9EqkaTHpRN+DGMTGdF4gJau2znbMFE5V0Ktm1758apcb0YGJJbeYBW5p46TrT7VoAyuh5gkn3nWnuHJDB2kAgHLOhiQCVOkgfKpGSsK4GHCvdPagsCct2Msd0hgkg1B6xn/wiywchlBY5jJ1Gs97ajv2xBGdo/lHEcRB5carulLNwWWUlMq5Toe/w2bOfXTnUtWb4c7xqS/UqIPVZh24jJJVhorzwPHQbb/nWyZ9a51htXUEnUxq8fhV2MG6zFtuMEYi5vwMFR7TWc8bk7R6fw74pDTY3CUb5svOm00CmAcxGpUCdtWJgecxSW+s+Jw9tmsorNbaEGUtObU7GWALcOFZpsE50ftyn3QUIHgM1waelWmLw6ymRGUMizmO8CJJ11BnYxoaUYbeyPiGvWrraqoyGFtNmIZSkkkypESdYBitZY6j4hsj27tnMVDhWLA5G+EmBv6x4moWKvWYC3LhUbyRcOvNYQg/1qz6M6fuhAtnEm4UQIv7qNANFzFNtBzq5OX5Ty4qP5i36O6pXruED22tFgBEu8aM823UpMd4ciI8aynSIa3cazds2Wa2cp1JUEawpOsRHAcfXT9E9ZsTaV7dtcOBqxZll2GaQWKXhB8xA2qtxV5r1xrv7RaljJCMjAeQhvrUx3OTs2UtkfSyrPSVzKqnssqSEAaCoMSNGEjSo74xiNMg/wDk/wDuatxh7xYIDmkTP7OpXc6ZuyiYE+tEbou79pLR/ktr9Mta2ZSbk7ZncPedTKEg7bkaec1OXFYvg59GqJgyuZsyoQFYnOdBlE8110jfXlNWlnBK0xh7LRocvasOehW8Qd6VIccs4qoyaA47t+7OZrjqpGVzME3BrkMgyo0MHbwqrXB3pOazcIMkwGBJPGSp8fer1rUNlNoQFULbHaroGOoI1+0TqeBnhUV+irX/AKWP5yPqhoi6JlcnbKzE2tMvY3NdwW1IHL933fODxrT4ts3SFpfuKJ8IDP8Al71UdhaBg2XBBg/vtoPLsxWtw2N6JW72t527UnvEFwMuUqImF5TrUZGd2jpQd/qj9lZNuPAJ5A1GwF2VMfDLZRxALFlB1OmUrH1qSvWPosroTmk6ZokZtABn1MaeZqNjum8K1xmS5bSTJUsqkNAzSuYwc06TXJz7H0sNVjzZotcKn3X0+pU9J22bF2YVioUmYJAPe3PA6LRulbDFQAD8ak+mvprFHfGWTr2qHfZxx340xsWCe64M6NBUyIMA8tYOnKqt8CyYmnkppqTXnnwglrSmvvSBqIluc0mIBM+0D1JA9ak9JVCNsC1UvWf/AGJHMj6iflNX2SqvpDGW0dczDMveCkNDEhlAYgaDWeenqLx/iRz/ABLIoaSbftX3MjhVVScpuCYjLo3CRpvrwqUL4GnaYgeGaPxo7rcec2Ls6zIIga8h2ego1vo9gBGOwgHKR/8AyrsZ8CXaYgnRVZtYhVzc+X63qR+x4jT9xcE/eVl321aPHjXagYpJqdw9pyKx0JjLnw2gPO7b09mJ+VO6U6n41cPduEW4VCxVCWdgNSFUW4JieNdVu4e23xIreag/UUL/ALOs8Fy/3WZf8pFG4KPmo3uIPj9kD5b12m31AtjfE3o3hcij6GofS/QGHm+XUhQQzAwAy9oucFonVSdQQeM1ZXOnCjW0shGRjlaLnwLlMN3iZEgDSN+NR81FrGPTqThRv2redxh/ly1k+m8JbsYvK1rPbBXIj52V0Nti1vUHNrr/ACGeJrY38e4yEMW7/fVTJKlWHdg6QxU+QqzsRdXI9pwMofOWIh1aMoObMpEA6QNT41LyorZRA6u2bNzD2rq2bSZlnuIoXQkAryUgSNToRvVrkqNZxqIih5SFA7ykDQDYxFEtY203w3FPkRWhBRdeNLKNyf8A5WP4VfYjo+0xOa1bbzRT9RVF16IOFkEGHH+R60++tLyU/wAKKq51TwLatg8P59ig+YFA/wC6GCHw4dV/uF0/ysK0qhcvGaAzVRJRWehlV+7Yt5FBEsFMzlyxoSYg7xvxotronuQ1uwXnVhbtrIzzGifd7vj4VaG5Te0rL5f1L3FBf6Mt3jcsIVt3LQQs6W1BCsgMDMCryfDQHnrVTe6ptwxLfzWk/wCUrV10a3/jMaY4WP8A9f8ASpzsKceBS5MGOpt5JCYhIJJ/2d0anUnS/vQL/VTE/ewrf3rTT/iJY1uLmKQcZ8qi3MZyAHzqtzBIwb9VMQsu1vDQveJXLIA1MTh99OY86gYzq/iS2YIpBzkRct/7yCxIa1ufOugYy09xGQbspCztqIFACAQPAU0+Sqs5yOrlwCDhHMcc9ok+zLTG6FdUYHD3YLLoFUnTNGnaGRqePKulLYnjVgL9sWlsm2SS85wGOpgCSNB66U7JaRyBeh7f2sPih5WW+utexWCwiLKnEBtO7dVwhEg65bYbhOh3Arp+EvK5cKHAViAWtsMwEd4SoABMwN4102B7d1pAKx46aePxAx6UyLfucbw4sR3sYVPIC9Hvlqyw9jC7ti1bxJM/8QrqioHgMu/MTHnBI+dNfq/hmPew9lvO2po4G5Saps57Y6OwzkBcTak7Tct/nUz/ALt2/wD1Vj/GK2q9WcGO8cHaUjYr3DqOBWOcRTx1ewp/3Fz0vN/10WSkvJtc1MLUhPjTC9SUOLV4NQy9NLUAI+EtlxcKKXGzRrw99vSpBueNRiaaaVDsk9rWK/tFtqXwl4gfu3Ov81tx/lNagk1muv1ucMp5OPmrD8qCl2bB7utR72VviVW8wD9aj2ruZVbmoPuAabcxAG5FAil65YZBhXZECkFfhEbmNhpxq4t4UZFi5cWQDowPAcWBoFzFqdNSD6U044nhFFj8Eo27wHcxJ/nQP9CtAu4vEL9qy/mWU+wBqO9ydyajs1Fk0Sz0w4+KyfNWSPmwPyobdPpxVx/I8e+WPnQFSafkUHWlY6K7AdMKMRiWzKM/ZRJHBSDFTjeDa5p9aV+jVQs8T2oDa7HLK6e1V7YC1uLSA+ACn3EGlY2gt7FIGC94liACFJXXTVhovrQcLjM7MAjgDYspAYcxp8qVcCOHaDyuMw9mkURsNcjS6wH8SWvqFBPvTEX3QnSItsucAgCBtIgQNdzoONRMXaV2LKuWeA/X4VmrzYm0ZOKtQxhQ9vLPgDmJPtUzEY6+jlAbT5dGkZTmBIOXWCP1rOjSByJt9xbEnOR/Cpb6DSo2M6WVLtu0bbnN8Vzs3KJpomYCM2up2UA8dhX+lr6/+WdttVKH1EMTQcL06qjJcTETJOZ7RGjahToAQNqES2Xog78dokT7fWii3tC+5P4zVL0L0thxcY3LyydApssjQNpaTmjXhxrQ2+lcMxyi9bngCwBI8AdaqxCJa8D8qiWOlbL3RZKXQ5kd62yrABLHMYGUAEzVrEjT3EGgYTBXQXm4XDcCAIAjkIPDhSsGiD0T+zYlHbD5sq3IDFrqgsogkaiVhjtI1q6FuwvdLKCOBuGRx4tNQuiOjr6doLmJa4CQUz20D2yJnVIVlII4Db0qPexF8MQcdhxBOjIsjwPf3pomi9dPE0zLFe7SmPdA3NIqxxIppcVFuYxeGvlUW5jDwEUDLMXKZcxCjciqe5dY7k0OKB0Wb49eEmqHrXiS+GcRoCp/4h+dTMpqJ0rhybF0ccjEeYEj6UhrsXoy+zWLWp+BR7KBUgVC6BtH9ntSCDB0Oh+I1P7JqQ32JmoltJoRugeNMGM4aCduftxp0KyXFsmM0xvEwD5gRNBudnsG18dPnTBcQj45/wAX/TTRZG4M/r5U6FaEbNwp1owZInzNecHht+uNVtrFY5mhcOI+895UA8/iJ34CltBs2F/p0sip2dsACAQJK+QNUV+zJJ38fyFCu9I9nCtL3DutrO6g+LlQPcLUi7eURMA8OZ9Bv7UOIKRR38Bis3cxip4NbDH/ADD5CrLo3D3VX95fF0+CBfxNUnSXVNbzl0xGItFjJCscsnchTqKPhurV23ljF34WfHNMfFmkcOWkmIqqRLZdXMMtzS5bVgCCARMEbHznjTMb0TYuks9skk5viYanjoRXreMZrnZKjrKli5U5YBAhTxbWYPInWIq2tJpxPt+VAEbC4VVUKqwo4Cf61MtwNNfPlSgDkaettRwPrP50go9cwyPowDeaz9agXurmEP8A5e3PNVVG4/aEHiePGoPWDoPtmUpiLtm5lgFQGWOGZTqOO0carsJ0D0pbJjHpcEd0NbVRPNiAWjwBHnQkIl3Oq9lSStu4m+ovXD7SGnw+lQ+irCA3Oxx18sil2V7mYqogHu5UMSR71pOhmu5ct5lNwb5FZV8Yzb/OpOrMYCx8LZlEkQDpxjz3qhFMLmMyzbxlo8s6wPUsWNRH6O6RYy+G6PuMd3OaWPP/AGVaPD9C2Axuph7AaYLi0gad9SBOtTgp5/KlwMpHxLc/ahNcootUpw9SXQAXKdNE7AUnZ0wEVaIEpMyjc0J8X90TSAORUPpPpZbFvN2Fy+5JARNojdjvrtpTbjsRJOnIEE+01O6GxaWmlrYeY+IaiOWulLbZSa8kPE9NYyziHw1ro2wyW4/e3W7NTmUPMkfxRCyZBpcT0r2iQ9i2l0j/AHLEqDyMgZhWj6ydI2roAFsEwO8QJE8PKsvct/6D8qrZyClx0Rlc8d/PapdnDg6kSfI/WmWra/05+o1A8iN6lIP1J/E1VEBUtDy9DSOsahT8gPU604HxP68KW9cAEkhRO5MT4ePlQFFX0v0pbwydpdMAnKBHHfjPLxPhVOf7RMGuhkeQkfJK017s7ilXUMp0IKkqfNWEGqu31VwStnTDgNwOXbyGYgUCYbBdYcPdy5TBYSAylSQeMEAx4gRUxozbanSotnoSwrB+zlwZBaWIOuoJJg6napZwzEgTlWNxueYnhw28aGCsJ2J5GnJYbh9DUixh1HAk+/vrRlQchSSGBa1/qSP9afm0HHx+VEfb8KELY4cd6YqKPFddsHbco10AqYOo3G4iZ+VSujumbOKzCzdByiWKlO6OBPEVG6W6nYHFnPcSHP21JUnTckaNw3Bpj9Tra4UYOzca1aJzXCCpe8f/AHGMaeAA0EbTILksuhOwIdrV0XJjM0yZE7+flwqD1ntdI6NgzbYAa22JBJk6hgQDPIkRFE6rdULWDLNbuXHLCO8ykKCZIVQNNhz2q8xCuF7kTMEkbDiQOJ2+vhR5DwYKz010tbRmvYaWAOVEV223lg7LrrAg/Sbjqv1nxOIcLdwN61O7MpCj+YhfbL61oFsnQM7Enxj6QKNdw4ZSpOhBB22OlFiC4nFm3auNlLQswNyQdAP4jsBxJFMt4tyAezjwLiR5whqsxvV21dCZrl4dmVZQHMAr8OhkD0irNFIAGZT4ldT5wQJ8gKKArrmMXMUQF2G+XZf7zHQeW/hSlX45V92+elDwrZFCqsAeO54k8yedCxJZuMeVZmgl+8y7P8tKEmIZh3tPLj4+FOKCJj1PH8KVQOX4f1NAxotzwp5tTT0J5D2n6zT2ukfe9IH40wArZrwta09MUCcuoPJh9J0PpXmI2OnIjQetUmJobfxIEAn03J4bfoUI3J+z/iMe4H50OxYIknVp1PE/kKb+zs7E3IKgyq65QNYMAjWNyeZqhck2yR/7fo0/8xNEgcMvufxah214KPQCaW4Y0O/Lc+3D1ikFDix8vTT8xUZLEks2ra6nWByHhTyxAJYjmZOg8z8qSwTE5dJkBtDGVV1G4Jyz4SAdQRQBhOs/WjHWrxtW7LLrCtDEMOaldW08fQUzDdO40W2vX7iwpjIqgmdPickxx08NxXSFI4rI8D+BB+tHtWLf3SPILTslowPVDrBjr9wBrLdnxuZSEjlrx/uyfIVvGYAFjr4czwA8TUnshwYfzAj+lB7GG72/A+HHLy4THhQ3YJUPR+dOzefsPzpvZEkAGNdSImPCdAfH9B6LBMExwkmfXWlQ7FIB5+wHz1oF7DswjcHcDiPHifLQHjUnMf8AXWkJHl/XamAKzajn+J9aOnlPMwQJ9TqPH5V4OZ70n2n+tEEcD7iP6fOkI9kB4CkKciR9Panx417LTAj52XcZh4DX24+ketS7TKQCDIOoOtDyRQACGMaLw8SdSfc7UCJb25pos+FMYzzLE7cOJmeA0obmDGQn0pAZDonrRYugQSGP2TE/ynZvSrdLgaI25fr9aVwCXU906cuFarqz17v2CqXMt1JAhzDDyu/9U+YqdpbZ1c66nhsOX9aVQOO363qN0V0nZxI/ct3gJa0/duJPMcR4iR41MOF8NfAj86TGmee4BSiyx+77n8q8LZHH3ZfxM0x7Y4t6CWP4D50IYG4QDwJHI6Dhvz1NOVSYY6DhzJ/KmEj7A/maD7DYfOmHzJPMmTTESTd2zlSeeob3E/OmMV4FgfIH5yPpQAlFVaoKBk6wQzL4GD/hOnzo5QKAQpM6DXjygAa14kDh7flSu4XX6caBUefDgxO418uGnAHfUa0TswIgfKQNeXE/rwLLFtxM695iDOpVjnA8CuYr4gDxiZb5fLYihiQ20GzaFgvoCfbSpMH7x968i+Ip/qPnQOgNxysTqJA8dSBPuR+hB9cXhJHl+oozR+vwFMce/AfnQIEeRYA8+B/Ly1p6ow8fnTAQIPpJ1r1/FqkZ7oSdpYAnyG5oAfNOCHlUP/tK1P8Ath/xflUmwc2qvm5w2b5Tp6inQrFvNlBJ1gExxMDbwoGFVmGa4deQ0UeEcfWaKyx9kEecH8j8vOnJHiPA6HT/AFGokUgHBR935UTTiPkPzpmGUiR4kj1JJ9ifajGgBguLzjz0H5U+ecEeG/pwoF1RxqmxWMNolrZJAElYkEcdOflr9CxMvyY21H08xwpAR+o/Og4a4GVXGmZQw9QDRpHjQB82sRQXszRVhhoaUHnWfRp32Lh8TcTLDkBTKme8n91t19DWv6A663c4S8c44NoH9eDfI+dY8imZJNNSDbXR3fB9I23WQQeccPMbinXrgIJG36/XrXF8H0xet6BiRwP2l8m/AzWy6u9dRHZ4hZ0+NAJ82TY+a+1VQmzZMdKHYuZh4qSrDlqYPkRB9aXD3EuLmtsHXmuseBG4PgaREGbMNG2njHLy8KQwyinK8nKNzx4etFt3P4R5gkT50ZBOyj0FAxn7Ll7zsDHLQf1pLduToPLwoxwxJljHhx9qbnnupoN54kcxyH18qCQlzLtO35abUdbp4jN/eA+u9R9EFOR2PCPPX6HT3NMVUHzfwj3NOW4OK/P8KGCefyH5U8PHAfT9e1ADzP2co9IPvQSCJnl8p1/Cihgdv6jx8vKhPeIkASSDAOgPMeBI+tADLtyFdlEuqsVHNgCQPeuDYjrRiDca6rDM5JlgGOvEzpO3gK7vYbSVBjjp3lPJ13B/121rD9b/AOzxMQzXsMwt3G1ZT/s3PEiNUY8YkHkNTTi6FJXycvPWLF5y/bvJ3g930X4R6Ctb1X6XxXZNiL11Si6W1IGYsTGbMIKqIbXXbaqmx1Dxi3QL1lhbGrMsMCAdlKzBPlpvGlG6TfEktbS1cCiFVFRoGWQCsCeJMjnTsmjoPVTrxbxHdYnxzfGuwzE/aSSBJ1E+lbVl4VxPqb1KxjX7V24hsW0YMS4h2E6qqHXUaSYEHjtXaWeASeNKTHFMUfTceexHh/WnDy9qDcuAMAeCHMOOpGT6P7Gnp7eX4k0gPPB0mkt5QI+LxME0pusNhPzpvankPaKB0Lv9NNgKb+1oPvHxCOw9CBBpxCt8Sz6z8jXjaT7z0CZ8x3gVaRpIB9wCfnNS8HdL6EaxOnEDUmPACm310XTYR7Gfxp9jCturBdN+EeO9D6KXLCvbI/KkWvW7ssqzJiIYZdvhjXciAJ+lShYLKHykKZCkgiSujAeVQ0i+UIFpMv6+f1ApyNzpWIqbaZdKSJHQ/Sd202YMwI2Zd/IjZh5ztW96J6923GXEKAfvqsr/ADJqV8xPpXPLAp16xp3dDVrJfZm8ddHa8JjLbgMpUqdmUKQfI61YQY+I+h/KuIdCdKXcMTqYO5X/AJkOhrb9GddbUgOwUHTMJKT/ABDdD5+sU+w67NlbJVSJ1YhT5Zhm8jln5UxFlifQfjS2nzpmSGmGUqQVbKQYB21iJ8aIg4jVW1B/A8jPCh9Ci1YIr3gTtHzJM/Qe1SA9KT4Ui2+TDyOh/KgZ4vSoWbRVJpTZbkP8Q/OktLkmGkn2oBuuhveUrKkEtEeBBzA+gJ8wKZiNvUR5zRcRibjRLbcY2HIew/WlRkdRLsYRBMnYeNJ+wL3ZKuMAZ1kRqN4M6eI8DpSgq3gfDT3FQsNiC0nLBYyZ+yNAFP8AFAEjYHNrUnJVGaCnD+IPypi67EHyYfnQxbWm9kZkH3oGSOxPgK8VjWJPNtAPTc/rWhrdI3cesURgpGoI8RqKAtg2Qb7zBJ5zx8or2UyI9fGjqoyiDIiD5c6HOviP1NJggtlWuZiDlRWKqNi2XRiTuBmkQPuneREW27zBJWOG/wA5qSBKnIYOp9SZPzn3oKLx402wih5ZuYPmJ+tJ2n8HsdP81LSTQNnz1i7PcY5QwnRhIK6QQRrM+PoeFRylwDSdojUQBp6+dWCORqP9fA0l21mByEBo1Vo13+A+u3zqbKKn9lVgp7QBjuDuDP6M1Y3Ma4tqruXKiF3gAkmIPiza+dRbaFD8EHx0PpIPyijXHzE6bjWeUSSf1zoasqMtoOzjhrmHgNPejBDGcEGZEAieGpHAfkarcRE1607LqNvl6iqogucM+tSTVdhL6Nvox0E7eh0o7sy6VlLH7Gkcnhkqaj4i3oSo1NeS7PnTg2tTG4stpSRbdWum8Rh27j5OJEgo3mh0J8teVdC6M61K0G6gtFjBOpsu397U229xz4EcrmpWHuvbVyhjMO8IBDRtIO9bLIn2YSxVyjta3UJAzBSdQrkCRwKNOVx4qTRmssN1Ncl6v9bGtgqCFXU9ldE2H55SfgbzI8ztW36H6fwV6F1w9w/Yzsin+4ykKfIgHwq9qI3M0JTwNeFpuUDmajnDg6dpe/8Ayv8AnSf9l2jqy5/77O/yYkUqQ9z9ht3G2gYUm8/3bcEDzb4V9TUe9ZdypuFQZ7ltfhtxrnY/bcRoYgEiBxq0VABAgDgAIHyqJcWGH91/8yUuPAnbCYa2AP1tTmbbx2H1PgP1ynynSgjV2HAW0j1L5/onyoALm5flTAx+8fc/nRKHcoHQQOeMEeIn+vzpyEfZMeBOh8AefgY8JoCmvEx+XOiwaCkEGV0PEc/yNRrt8famBsQNU8HH3P4uA30E0UXNhMg/AeO05Tz0kg+BnYSiyhB3k60AERSsAyDwPPyPGnXBOux5jY+YqQTI8D6g/wBf1woVtM2xAPIn6GigsaJ5T4jX+tJPn7GldWXcEeVDOKPP5UDOCW1kwuw5kE76bRJiOFeYU63b03nNqf8AERv6b+NEuwREajSfwoaEmD7QEENy34+E8xUDFDLud/n5VKYUtkjY6jlUop8kDD2wTryJ9BUh7WfUiOQ/Oi3FCklQSAdzExypquSe7BB1HAxr/X2qyCqugTpUi1iysK2o+Ypt22Dcyr8ufGm4i0ZH6JooCwW4G1Un8fbhTxcqpRmXUSP186ssFmuAmPh3I2109KlqylJrokK1WWGMjnVQykfjVhgrvDY8jWU4Nco2hNPhk/KIiKi3bB4HT7p29OVGD15nrKM3FmkoJkroXrHesOLbMGT7KOdR4K+/pt4V0XorptLmitDfcbf05+lcqu4VGMsJ0jWi2L9y1GViyjZWM+k7xW/zEzDY0doW/O+lCdtQfHXyP9YPkKwvR/W3SJzc1bRx5H7Xz4bVo+r3S9rEk9m4YjRkOjDzXiPESKtEOi5FCYkEMBMSCPvKfiA8dAR5RpNSDbPr9R+Y/rxMNiaYrs8CBBBlT8J5/kaeyzQ07s8juOBPP+E+PuDpTxbH2Wjwbb32/W1DBMHk1IqNlLPkmNJFS2wzzw89Yry4Ihs061PZVi4jDhLW8le9P8SnN9RFBxl3v5Qdj9CalsxEBuYJ8SNRPhMH0FVeLCs4uKwMyCBvPMjeql0RHllhYJIIG4Mjz3HpQsWoJDrPeHDT3p/R40J8qrcTijcuJh0JGVFuXmGhVDoltTwdyG13Cq0QSpCXKG3TLfD3nA1YHz/W9ebEW51A/XrUEHNoNFGgA0ED8PCnxTCji6EqigHSZIOoJGokbGMx9zQws8oE8ANdN433G9er1UIMbX7srA1J1O4gcP8AF8qgMoB024eXClr1SxoWKVcOCrZAFaJJkwdY29aSvUkMprN3IGjc6a/qa8LsTOpr1eqyTzPIiN6TB3mRgR7HUe1LXqQFrc6RXsz3TmBAPI68/IHnR1hwGGxE/nXq9SGEt3DGutPS/Xq9WeSK7NMcn0GzUuevV6uY3FCgkGNRqPMbVVti2XEM2xzSCndKneVilr1dWFumc2VHROh+vN23lt4pe1WFIuLpcWQCJ2DHUcjvqa3/AGWbUaHKG8wdpHA/rwpK9WzRigIfgaWOWler1QWNW6w+77a079qbwr1epWVRGva71CuLDCOOlLXqllInq3dC89PkST7A+sVT9BGWxtw7tibieS2Ut21HyJ9a9Xq0XRl5LK0NKQmvV6kWf//Z" alt="Plasma CNC Cutting" />
                        </div>
                        
                        <!-- Profile Cutting -->
                        <div class="product-thumbnail" onclick="updateProduct('profile')">
                            <img src="images/profile-cutting.jpg" alt="Profile Cutting Services" />
                        </div>
                        
                        <!-- All Products -->
                        <div class="product-thumbnail bg-gradient-to-br from-blue-600 to-blue-800" onclick="showAllProducts()">
                            <div class="product-placeholder text-white">
                                <i class="fas fa-boxes"></i>
                                <span class="font-semibold mt-2">View All Products</span>
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

        <!-- Product Details Section -->
        <section id="products" class="py-20 bg-slate-50 reveal">
            <div class="max-w-7xl mx-auto px-4">
                <div class="bg-white p-8 md:p-12 rounded-3xl border border-slate-100 transition-all duration-500 shadow-lg" id="product-card">
                    <div class="prose prose-slate max-w-none">
                        <!-- Product Image Section -->
                        <div class="mb-12 reveal stagger-delay-1">
                            <div class="flex flex-col lg:flex-row gap-8 items-start">
                                <!-- Product Image -->
                                <div class="flex-1">
                                    <div class="product-image-container" id="product-image-container">
                                        <img src="long weldneck.png" alt="Long Weld Neck Flange" id="product-main-image" />
                                    </div>
                                </div>
                                
                                <!-- Product Info -->
                                <div class="flex-1">
                                    <div class="bg-gradient-to-br from-slate-900 to-blue-900 rounded-2xl p-6 text-white h-full">
                                        <h4 class="text-xl font-bold mb-4 flex items-center gap-2">
                                            <i class="fas fa-info-circle text-blue-300"></i>Product Information
                                        </h4>
                                        <div class="space-y-4 mb-6">
                                            <div>
                                                <div class="text-sm text-blue-300 mb-1">Current Product</div>
                                                <div class="font-bold text-lg" id="current-product-name">Long Weld Neck Flange</div>
                                            </div>
                                            <div>
                                                <div class="text-sm text-blue-300 mb-1">Reference Code</div>
                                                <div class="font-medium">ASMEB16.5-900-DN15</div>
                                            </div>
                                            <div>
                                                <div class="text-sm text-blue-300 mb-1">Standard</div>
                                                <div class="font-medium">ASME B16.5</div>
                                            </div>
                                            <div>
                                                <div class="text-sm text-blue-300 mb-1">Nominal Diameter</div>
                                                <div class="font-medium">DN15 (1/2")</div>
                                            </div>
                                            <div>
                                                <div class="text-sm text-blue-300 mb-1">Pressure Rating</div>
                                                <div class="font-medium">Class 900 (150#)</div>
                                            </div>
                                        </div>
                                        
                                        <div class="space-y-3">
                                            <h5 class="font-bold text-lg mb-2">Available Formats</h5>
                                            <div class="text-sm text-slate-300 space-y-2">
                                                <div class="flex items-center gap-2">
                                                    <i class="fas fa-file-pdf text-red-300"></i>
                                                    <span>Technical Data Sheets (PDF)</span>
                                                </div>
                                                <div class="flex items-center gap-2">
                                                    <i class="fas fa-file-alt text-blue-300"></i>
                                                    <span>Specification Documents</span>
                                                </div>
                                                <div class="flex items-center gap-2">
                                                    <i class="fas fa-download text-green-300"></i>
                                                    <span>CAD Drawings (DWG/STEP)</span>
                                                </div>
                                                <div class="flex items-center gap-2">
                                                    <i class="fas fa-clipboard-check text-yellow-300"></i>
                                                    <span>Certification Documents</span>
                                                </div>
                                            </div>
                                        </div>
                                        
                                        <div class="mt-6 pt-6 border-t border-slate-700">
                                            <button onclick="downloadProductFiles()" class="w-full py-3 bg-blue-600 text-white font-bold rounded-xl hover:bg-blue-700 transition mb-3">
                                                <i class="fas fa-download mr-2"></i>Download Technical Files
                                            </button>
                                            <button onclick="requestCustomQuote()" class="w-full py-3 bg-slate-800 text-white font-bold rounded-xl hover:bg-slate-700 transition">
                                                <i class="fas fa-file-alt mr-2"></i>Request Custom Quote
                                            </button>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                        
                        <div class="flex flex-col md:flex-row md:items-center justify-between gap-6 mb-10">
                            <div>
                                <h3 class="text-4xl font-bold text-slate-900" id="p-title">Long Weld Neck Flange (LWN)</h3>
                                <div class="flex items-center gap-4 mt-2">
                                    <span class="px-3 py-1 bg-blue-50 text-blue-700 rounded-full text-xs font-bold">ASME B16.5</span>
                                    <span class="px-3 py-1 bg-green-50 text-green-700 rounded-full text-xs font-bold">Class 900</span>
                                    <span class="px-3 py-1 bg-purple-50 text-purple-700 rounded-full text-xs font-bold">CAD Available</span>
                                    <span class="px-3 py-1 bg-orange-50 text-orange-700 rounded-full text-xs font-bold">DN15</span>
                                </div>
                            </div>
                            <div class="flex gap-3">
                                <button onclick="openOrderModal()" class="px-6 py-3 bg-gradient-to-r from-blue-600 to-blue-800 text-white rounded-lg font-bold shadow-md hover:from-blue-700 hover:to-blue-900 transition flex items-center gap-2">
                                    <i class="fas fa-shopping-cart"></i>Order Now
                                </button>
                                <button onclick="downloadProductFiles()" class="px-6 py-3 bg-slate-100 text-slate-700 rounded-lg font-bold hover:bg-slate-200 transition flex items-center gap-2">
                                    <i class="fas fa-download"></i>Download Specifications
                                </button>
                            </div>
                        </div>
                        <p class="text-slate-600 text-xl leading-relaxed mb-10 max-w-4xl" id="p-desc">
                            Long Weld Neck flanges are specifically designed for pressure vessel applications and high-pressure piping systems. Featuring an extended neck that provides reinforcement and stress distribution, these flanges are ideal for critical applications where reliability is paramount. Our ASME B16.5 Class 900 DN15 model represents precision engineering for demanding industrial environments.
                        </p>
                        
                        <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-6 mb-12" id="p-features">
                            <!-- Features will be populated by JavaScript -->
                        </div>
                        
                        <!-- Additional Product Info -->
                        <div class="bg-blue-50 rounded-2xl p-6 mb-8">
                            <h4 class="text-xl font-bold text-slate-900 mb-4 flex items-center gap-2">
                                <i class="fas fa-cube text-blue-600"></i>Documentation Available
                            </h4>
                            <div class="grid md:grid-cols-2 gap-6">
                                <div>
                                    <h5 class="font-bold text-slate-800 mb-2">Technical Documents</h5>
                                    <ul class="text-slate-600 space-y-1">
                                        <li class="flex items-start gap-2"><i class="fas fa-check text-green-500 mt-1"></i>Detailed technical data sheets</li>
                                        <li class="flex items-start gap-2"><i class="fas fa-check text-green-500 mt-1"></i>Material certification (EN 10204 3.1)</li>
                                        <li class="flex items-start gap-2"><i class="fas fa-check text-green-500 mt-1"></i>Dimensional drawings with tolerances</li>
                                        <li class="flex items-start gap-2"><i class="fas fa-check text-green-500 mt-1"></i>Pressure-temperature ratings</li>
                                        <li class="flex items-start gap-2"><i class="fas fa-check text-green-500 mt-1"></i>Installation and maintenance guides</li>
                                    </ul>
                                </div>
                                <div>
                                    <h5 class="font-bold text-slate-800 mb-2">File Formats Available</h5>
                                    <ul class="text-slate-600 space-y-1">
                                        <li class="flex items-start gap-2"><i class="fas fa-check text-green-500 mt-1"></i>PDF (Technical data sheets)</li>
                                        <li class="flex items-start gap-2"><i class="fas fa-check text-green-500 mt-1"></i>STEP (CAD integration)</li>
                                        <li class="flex items-start gap-2"><i class="fas fa-check text-green-500 mt-1"></i>DWG (AutoCAD compatible)</li>
                                        <li class="flex items-start gap-2"><i class="fas fa-check text-green-500 mt-1"></i>IGES (Engineering design)</li>
                                        <li class="flex items-start gap-2"><i class="fas fa-check text-green-500 mt-1"></i>Excel (Material specifications)</li>
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

        <!-- Product Gallery Section -->
        <section id="product-gallery" class="py-24 bg-white reveal">
            <div class="max-w-7xl mx-auto px-4">
                <div class="text-center mb-16">
                    <span class="text-blue-600 font-bold uppercase tracking-widest text-sm">Product Gallery</span>
                    <h2 class="text-4xl md:text-5xl font-bold text-slate-900 mt-2 mb-4">Explore All Products</h2>
                    <p class="text-slate-600 max-w-3xl mx-auto text-lg">Click on any product to view detailed specifications and technical information</p>
                </div>
                
                <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
                    <!-- Long Weld Neck -->
                    <div class="gallery-product-card bg-slate-50 rounded-3xl overflow-hidden border border-slate-200 hover:border-blue-300 transition-all duration-300">
                        <div class="product-image-container" style="height: 250px;">
                            <img src="data:image/jpeg;base64,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" alt="Long Weld Neck Flange" style="object-fit: contain;">
                        </div>
                        <div class="p-6">
                            <h4 class="font-bold text-xl text-slate-900 mb-2">Long Weld Neck Flange</h4>
                            <p class="text-slate-600 mb-4">ASME B16.5 Class 900 DN15 with extended hub design</p>
                            <div class="flex gap-3">
                                <button onclick="updateProduct('lwn')" class="flex-1 py-2.5 bg-blue-600 text-white rounded-lg font-medium hover:bg-blue-700 transition text-sm">
                                    <i class="fas fa-info-circle mr-2"></i>View Details
                                </button>
                                <button onclick="openOrderModalWithProduct('lwn')" class="flex-1 py-2.5 bg-slate-200 text-slate-700 rounded-lg font-medium hover:bg-slate-300 transition text-sm">
                                    <i class="fas fa-shopping-cart mr-2"></i>Order
                                </button>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Weld Neck Flange -->
                    <div class="gallery-product-card bg-slate-50 rounded-3xl overflow-hidden border border-slate-200 hover:border-blue-300 transition-all duration-300">
                        <div class="product-image-container" style="height: 250px;">
                            <img src="data:image/jpeg;base64,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" alt="Weld Neck Flange" style="object-fit: contain;">
                        </div>
                        <div class="p-6">
                            <h4 class="font-bold text-xl text-slate-900 mb-2">Weld Neck Flange</h4>
                            <p class="text-slate-600 mb-4">High-pressure applications with tapered hub design</p>
                            <div class="flex gap-3">
                                <button onclick="updateProduct('wnf')" class="flex-1 py-2.5 bg-blue-600 text-white rounded-lg font-medium hover:bg-blue-700 transition text-sm">
                                    <i class="fas fa-info-circle mr-2"></i>View Details
                                </button>
                                <button onclick="openOrderModalWithProduct('wnf')" class="flex-1 py-2.5 bg-slate-200 text-slate-700 rounded-lg font-medium hover:bg-slate-300 transition text-sm">
                                    <i class="fas fa-shopping-cart mr-2"></i>Order
                                </button>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Slip-On Flange -->
                    <div class="gallery-product-card bg-slate-50 rounded-3xl overflow-hidden border border-slate-200 hover:border-blue-300 transition-all duration-300">
                        <div class="product-image-container" style="height: 250px;">
                            <img src="https://bfnf.in/public/image/f249688537eb6cd7c908424877322dfc.png" alt="Slip-On Flange" style="object-fit: contain;">
                        </div>
                        <div class="p-6">
                            <h4 class="font-bold text-xl text-slate-900 mb-2">Slip-On Flange</h4>
                            <p class="text-slate-600 mb-4">Cost-effective solution for standard pressure duty</p>
                            <div class="flex gap-3">
                                <button onclick="updateProduct('slipon')" class="flex-1 py-2.5 bg-blue-600 text-white rounded-lg font-medium hover:bg-blue-700 transition text-sm">
                                    <i class="fas fa-info-circle mr-2"></i>View Details
                                </button>
                                <button onclick="openOrderModalWithProduct('slipon')" class="flex-1 py-2.5 bg-slate-200 text-slate-700 rounded-lg font-medium hover:bg-slate-300 transition text-sm">
                                    <i class="fas fa-shopping-cart mr-2"></i>Order
                                </button>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Blind Flange -->
                    <div class="gallery-product-card bg-slate-50 rounded-3xl overflow-hidden border border-slate-200 hover:border-blue-300 transition-all duration-300">
                        <div class="product-image-container" style="height: 250px;">
                            <img src="https://bfnf.in/public/image/3ea4a78a91ab1bac509e181ff3c73f54.png" alt="Blind Flange" style="object-fit: contain;">
                        </div>
                        <div class="p-6">
                            <h4 class="font-bold text-xl text-slate-900 mb-2">Blind Flange</h4>
                            <p class="text-slate-600 mb-4">System closure and pressure isolation</p>
                            <div class="flex gap-3">
                                <button onclick="updateProduct('blind')" class="flex-1 py-2.5 bg-blue-600 text-white rounded-lg font-medium hover:bg-blue-700 transition text-sm">
                                    <i class="fas fa-info-circle mr-2"></i>View Details
                                </button>
                                <button onclick="openOrderModalWithProduct('blind')" class="flex-1 py-2.5 bg-slate-200 text-slate-700 rounded-lg font-medium hover:bg-slate-300 transition text-sm">
                                    <i class="fas fa-shopping-cart mr-2"></i>Order
                                </button>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Puddle Flange -->
                    <div class="gallery-product-card bg-slate-50 rounded-3xl overflow-hidden border border-slate-200 hover:border-blue-300 transition-all duration-300">
                        <div class="product-image-container" style="height: 250px;">
                            <img src="data:image/jpeg;base64,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" alt="Puddle Flange" style="object-fit: contain;">
                        </div>
                        <div class="p-6">
                            <h4 class="font-bold text-xl text-slate-900 mb-2">Puddle Flange</h4>
                            <p class="text-slate-600 mb-4">Waterproofing for pipe penetrations</p>
                            <div class="flex gap-3">
                                <button onclick="updateProduct('puddle')" class="flex-1 py-2.5 bg-blue-600 text-white rounded-lg font-medium hover:bg-blue-700 transition text-sm">
                                    <i class="fas fa-info-circle mr-2"></i>View Details
                                </button>
                                <button onclick="openOrderModalWithProduct('puddle')" class="flex-1 py-2.5 bg-slate-200 text-slate-700 rounded-lg font-medium hover:bg-slate-300 transition text-sm">
                                    <i class="fas fa-shopping-cart mr-2"></i>Order
                                </button>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Plasma CNC -->
                    <div class="gallery-product-card bg-slate-50 rounded-3xl overflow-hidden border border-slate-200 hover:border-blue-300 transition-all duration-300">
                        <div class="product-image-container" style="height: 250px;">
                            <img src="data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAkGBxITEhUTExMWFhUXGBcXFxgYGBgaGBgYGBcXGBcYGBgeHSggGBolHRgYIjEjJSkrLi4uFyAzODMtNygtLisBCgoKDg0OGhAQGi0fHyUtLS0tLS0tLS0tLS0tLSstLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLSstLS0tLf/AABEIANYA6wMBIgACEQEDEQH/xAAcAAABBQEBAQAAAAAAAAAAAAADAQIEBQYHAAj/xABIEAACAQIEAggDBQUFBQgDAAABAhEAAwQSITFBUQUGEyJhcYGRMqGxQlLB0fAUI2KC4QdykrLxM0OiwtIVFiREVGOD4pOz0//EABoBAAMBAQEBAAAAAAAAAAAAAAABAgMEBQb/xAAtEQACAgEEAQIEBgMBAAAAAAAAAQIRAwQSITFBIlEFE2GRMkJScYGhseHwFf/aAAwDAQACEQMRAD8A5rccfeFQVP7xY51pTav8UsH0blFVN/B3e0DNbGYggZAY0Gs8jB/CsoyTPRy6LLj9Vf0yy6GuxdGkyCI5zWnvWGAAjifwrIYOzc0cI3rofYmRVrf6zFWVIYOIkEKB4d4mKxnG3we1pdUseL18fuW6WSeFYbtHG7H3rR2+sJuSBuDG67+GuvpTOkuhwlhL/aORcbLlIAIP2uJ0Hz8NqeOL8o5fiOp3RjOEvszK4m43OndH2nuBUQZmJIAEanXTWr3rL1ZNjC2sR2pc3UFxVFtiAJUMHcDKpE8d4oPVrDrbz3mGZbZhQwIzMeYOwj8a2pUeT8+bfLssrds2kt2kGa6RIA2Wd3PuQJ86tkwwsWXJ77ELmPOGWAJ4Cs5gukwS7FwHaSSSATGo8ttqlX+kmdAuaRtv+NZSvo9PBBRi8sncq4+gl25bd5IhMhMRxJAJ0oBWwNVbKeYJHj+XtVhgeiXvdoihu1S13bYSWZ+01TWCDUHFdW8cvxYPED/4Xj3intvyc2PWbW3KClbsq+lRnkm4WJ0ktJI03PHYVAwVrvfrwp/SFl0JV0ZSDEEEEHkRuDXujhETVpUiZZYZcsWo7ToPVOBYaT9ox7D8Jqv6UsY1GZrFy9lJkBXLROpGUiBUjoK5lw7knYz57Uyx0jd1i4OMA5SBWcLt0d2teNQip3/B7B9P9LWtQzkZgIe1mMeelWnSPXe+ytav2MJdm0Stzs2DoWAC6NswJB9KjL0nf/gbzH5RVN1i6RZ4VgARq0TG2g19/atHZ58VgXKk7/72If7XetgvZXK3ZtLAkFUIysZkZTHEcTUnqrj7oUrZTO4ZcilgoLFtACRG/OKjdB9PrYvF2s9pmtvbABGhcABoIMxFTepYyOg5Oh9iDUyfp5OnTK89Qlarv7+53HBdI9HXQLN65hjeWZt3Gt5xqSAVJk6EcONcz69dRry3buIt2z+zA5lKXFKoumgTNoJnQCK0t7pPAXVyXjeDrJbKWy6EsYWSp0H3eNchx+Et27twWrjFGJgRkmdtFAA34AVpfpOXHFrLKqffD/cndXgVYAkk5xvy1J+ZrrnRty4uGLi0rJEhs4DaASCrACJH3uNci6s4YqwDGWEkzrqdB8if+HjIrTdJft4tP2Rs3bHxGzcWSsKMxDAhtYmJ41mn6zo2btPwvP8ARtcD0Q2HvM5YsrFXzqmWCRBAkkEiJ/CrnqvjlN/EPJi4wILCIylwddRvybidBx5n1GuItp3fPa1uOwXXLbCEhLcyWaRAkbtGtdP6n9DvZVc926XdVLLK5EY5mdR3QYk8ddKqCfRw5+H34NDi7rAgKobjq0fga4L/AGjdOftONeAAtodiIMzkLZjMCe8W9BXWOvnWY4HDXrwQswK27eoC53Ayk6zAknbhXzNcxBjLJJO5Op8T5mt8a9VnJLqiwtXczZuGw8uJr6V6t4m9iMLYvZ0l7ak9w/FEN9rmDXzRhLojYj00r6C/s3xlwdHWAEBA7QTmI2u3OGU1eVWiYdnIxZvZc/YXMuYrP7v4huPjpr9ou9m4NM2y/Dz+KtPhs37K4b4luIx/nSD5a1RYbGMr9leZSe92bgrlcGRlIGiuJiK5fkxPZ/8AZ1Hsvt/sjh7mn7m7qJGg1B/mqk61Ydg1vtLbWyVMZxEieEHz/Rrc9G95bKkwcuQ78NNY14VT/wBoKArZbOGK9yAzK47usgjK2oEkHl4y1CMWTl1uo1GFpxVeWl0ZPot0TMDBBj4e8ePtUu6zfCIK7eOpJAJ8JMeZFH6tW81whgxGQnVViQR9rerzFdG5iCsDz02pN1I2wYZZtJVXT/k3v9ntxL3R9u3cCuhDIyOAykB2EFToRoN6z/TeH7fHYoqABas33WAI7RLXZWz5ggGs1hkbDWyHvZTmJUIbhBEkmYXQ6/Wtd1YuK14IRJu4e9Mic372J8TA18xzpbrZx5tLLDCMpPl+K5Rxa7iGdbY4IGyxv3mLEk85NbTorGNc6Mt2smbsMSWbKCWyXFuXHLiDIi22xGwnjOHwgkfrlWk6sYwo7KWOW4lxGWZBBtOJZPi0DNqDx30rajhs2PVTFdljrF9rgi72jXJ1KhbmpeRpMSIn612m5i1uW1dGDK0EEcRrXA8PhxffDoYtW8iLdug/CrdmXYljlB+OCBxk6DTrLIjYI2sDdCx3bb520IcMxzwS094zrM8jWL4Zp2jk/wDaTftt0heR8N2hR0IYXCrNmS25UhVOh25xsRWdPQrLdVXVsMpJEuWuZY1+FUkxIHl71u+urdliA5uk3WRYEKwzpbtqcpgGJ1kgxM6VW9XusWZv2e5hrTBm1LkLGgO50I0kbb1olwW5tdoqOoWKsNjDaxhd8ORcChUuSzgjJ3bUvsG0E+NdU6MToO+WsYe3YdpGZexYGQY1LpodNdd99TXIeq8DESIlQxXfQ7TvroTuK1vQY7K7nGpIIM8ZJJn1j2qZUjswYcmeLk5ceDRdb+h8GtxMLZw9mxFp8Vib62kz2sPb0At6aXHbug8IOhrlWKtotsGZfiDJjidePHjOtdC6MvW7mLujEMvZ3Ww4dn07lkPeyiODXDbBHImud9OXLTYm8LK5LFu4yIMzPnVGK5yzy0tBPgCPM3GNnDkTxyqRO64dXewbtEZFXKgyicwbKMxJJ3JPDgducboHFFcTh1Pwvcthm17oZwpMeAM1O6dS1jS+JU2LBAzPnuHMZZUUEhPEVX2ejbtjEWluFWJKsuSTpmIA1UGdDwpNccl4ZzjL0Ovqa/ofpcdpdS9dcJlTIAqfaa5MysxAFR+muibFy5OFYhgoLPcMgksBCKqwGC5jPONNZqqw+Bv52m0wkLqdtMxOv8wrQ4CyQuYkd7aOA21030rGWSnwetpvh8MsVKUnbu0Yp1vYQjMJkwCDMnc7iaPd6SxTM0QA3nt7x8oqy60Wwz2V5vP+UfjRLtoKJ8h6kwPmaW7izV6JOcsbfpjX+LNH1NWx+5e86ItrvOHcfvLwM22VTrkXusf4iu2U11HoXpKyQAt1WICnunN3WBCtpwOV4PHKeVcRXDFgAIkcyBvvqSAOFa/qtfuWLFzNiMN2rMoRbl1RltKrgCRpINxiJJqoM8/W6TJGfCbsrv7ausaXV/YrTd5Lq3LummzhVngRKEiOI10g8nFlV1DSfPX0rWP1Lvu9x7uMwuZy7yMSHOYkmWJgd7znXzqn6e6AvYZAzXLF3UhjbuhwBAI00bnuP69UXFHC8GV/lf2ZCwzMWCgySYAjWToAOMkxX031YVcPhLFkhgyW1DwjkZyJfXLr3ia+dOoWOC46w7LpbYvpO6o5XTkWCj1rsvR3XMrbUXXzPEsSrHVu9EqkaTHpRN+DGMTGdF4gJau2znbMFE5V0Ktm1758apcb0YGJJbeYBW5p46TrT7VoAyuh5gkn3nWnuHJDB2kAgHLOhiQCVOkgfKpGSsK4GHCvdPagsCct2Msd0hgkg1B6xn/wiywchlBY5jJ1Gs97ajv2xBGdo/lHEcRB5carulLNwWWUlMq5Toe/w2bOfXTnUtWb4c7xqS/UqIPVZh24jJJVhorzwPHQbb/nWyZ9a51htXUEnUxq8fhV2MG6zFtuMEYi5vwMFR7TWc8bk7R6fw74pDTY3CUb5svOm00CmAcxGpUCdtWJgecxSW+s+Jw9tmsorNbaEGUtObU7GWALcOFZpsE50ftyn3QUIHgM1waelWmLw6ymRGUMizmO8CJJ11BnYxoaUYbeyPiGvWrraqoyGFtNmIZSkkkypESdYBitZY6j4hsj27tnMVDhWLA5G+EmBv6x4moWKvWYC3LhUbyRcOvNYQg/1qz6M6fuhAtnEm4UQIv7qNANFzFNtBzq5OX5Ty4qP5i36O6pXruED22tFgBEu8aM823UpMd4ciI8aynSIa3cazds2Wa2cp1JUEawpOsRHAcfXT9E9ZsTaV7dtcOBqxZll2GaQWKXhB8xA2qtxV5r1xrv7RaljJCMjAeQhvrUx3OTs2UtkfSyrPSVzKqnssqSEAaCoMSNGEjSo74xiNMg/wDk/wDuatxh7xYIDmkTP7OpXc6ZuyiYE+tEbou79pLR/ktr9Mta2ZSbk7ZncPedTKEg7bkaec1OXFYvg59GqJgyuZsyoQFYnOdBlE8110jfXlNWlnBK0xh7LRocvasOehW8Qd6VIccs4qoyaA47t+7OZrjqpGVzME3BrkMgyo0MHbwqrXB3pOazcIMkwGBJPGSp8fer1rUNlNoQFULbHaroGOoI1+0TqeBnhUV+irX/AKWP5yPqhoi6JlcnbKzE2tMvY3NdwW1IHL933fODxrT4ts3SFpfuKJ8IDP8Al71UdhaBg2XBBg/vtoPLsxWtw2N6JW72t527UnvEFwMuUqImF5TrUZGd2jpQd/qj9lZNuPAJ5A1GwF2VMfDLZRxALFlB1OmUrH1qSvWPosroTmk6ZokZtABn1MaeZqNjum8K1xmS5bSTJUsqkNAzSuYwc06TXJz7H0sNVjzZotcKn3X0+pU9J22bF2YVioUmYJAPe3PA6LRulbDFQAD8ak+mvprFHfGWTr2qHfZxx340xsWCe64M6NBUyIMA8tYOnKqt8CyYmnkppqTXnnwglrSmvvSBqIluc0mIBM+0D1JA9ak9JVCNsC1UvWf/AGJHMj6iflNX2SqvpDGW0dczDMveCkNDEhlAYgaDWeenqLx/iRz/ABLIoaSbftX3MjhVVScpuCYjLo3CRpvrwqUL4GnaYgeGaPxo7rcec2Ls6zIIga8h2ego1vo9gBGOwgHKR/8AyrsZ8CXaYgnRVZtYhVzc+X63qR+x4jT9xcE/eVl321aPHjXagYpJqdw9pyKx0JjLnw2gPO7b09mJ+VO6U6n41cPduEW4VCxVCWdgNSFUW4JieNdVu4e23xIreag/UUL/ALOs8Fy/3WZf8pFG4KPmo3uIPj9kD5b12m31AtjfE3o3hcij6GofS/QGHm+XUhQQzAwAy9oucFonVSdQQeM1ZXOnCjW0shGRjlaLnwLlMN3iZEgDSN+NR81FrGPTqThRv2redxh/ly1k+m8JbsYvK1rPbBXIj52V0Nti1vUHNrr/ACGeJrY38e4yEMW7/fVTJKlWHdg6QxU+QqzsRdXI9pwMofOWIh1aMoObMpEA6QNT41LyorZRA6u2bNzD2rq2bSZlnuIoXQkAryUgSNToRvVrkqNZxqIih5SFA7ykDQDYxFEtY203w3FPkRWhBRdeNLKNyf8A5WP4VfYjo+0xOa1bbzRT9RVF16IOFkEGHH+R60++tLyU/wAKKq51TwLatg8P59ig+YFA/wC6GCHw4dV/uF0/ysK0qhcvGaAzVRJRWehlV+7Yt5FBEsFMzlyxoSYg7xvxotronuQ1uwXnVhbtrIzzGifd7vj4VaG5Te0rL5f1L3FBf6Mt3jcsIVt3LQQs6W1BCsgMDMCryfDQHnrVTe6ptwxLfzWk/wCUrV10a3/jMaY4WP8A9f8ASpzsKceBS5MGOpt5JCYhIJJ/2d0anUnS/vQL/VTE/ewrf3rTT/iJY1uLmKQcZ8qi3MZyAHzqtzBIwb9VMQsu1vDQveJXLIA1MTh99OY86gYzq/iS2YIpBzkRct/7yCxIa1ufOugYy09xGQbspCztqIFACAQPAU0+Sqs5yOrlwCDhHMcc9ok+zLTG6FdUYHD3YLLoFUnTNGnaGRqePKulLYnjVgL9sWlsm2SS85wGOpgCSNB66U7JaRyBeh7f2sPih5WW+utexWCwiLKnEBtO7dVwhEg65bYbhOh3Arp+EvK5cKHAViAWtsMwEd4SoABMwN4102B7d1pAKx46aePxAx6UyLfucbw4sR3sYVPIC9Hvlqyw9jC7ti1bxJM/8QrqioHgMu/MTHnBI+dNfq/hmPew9lvO2po4G5Saps57Y6OwzkBcTak7Tct/nUz/ALt2/wD1Vj/GK2q9WcGO8cHaUjYr3DqOBWOcRTx1ewp/3Fz0vN/10WSkvJtc1MLUhPjTC9SUOLV4NQy9NLUAI+EtlxcKKXGzRrw99vSpBueNRiaaaVDsk9rWK/tFtqXwl4gfu3Ov81tx/lNagk1muv1ucMp5OPmrD8qCl2bB7utR72VviVW8wD9aj2ruZVbmoPuAabcxAG5FAil65YZBhXZECkFfhEbmNhpxq4t4UZFi5cWQDowPAcWBoFzFqdNSD6U044nhFFj8Eo27wHcxJ/nQP9CtAu4vEL9qy/mWU+wBqO9ydyajs1Fk0Sz0w4+KyfNWSPmwPyobdPpxVx/I8e+WPnQFSafkUHWlY6K7AdMKMRiWzKM/ZRJHBSDFTjeDa5p9aV+jVQs8T2oDa7HLK6e1V7YC1uLSA+ACn3EGlY2gt7FIGC94liACFJXXTVhovrQcLjM7MAjgDYspAYcxp8qVcCOHaDyuMw9mkURsNcjS6wH8SWvqFBPvTEX3QnSItsucAgCBtIgQNdzoONRMXaV2LKuWeA/X4VmrzYm0ZOKtQxhQ9vLPgDmJPtUzEY6+jlAbT5dGkZTmBIOXWCP1rOjSByJt9xbEnOR/Cpb6DSo2M6WVLtu0bbnN8Vzs3KJpomYCM2up2UA8dhX+lr6/+WdttVKH1EMTQcL06qjJcTETJOZ7RGjahToAQNqES2Xog78dokT7fWii3tC+5P4zVL0L0thxcY3LyydApssjQNpaTmjXhxrQ2+lcMxyi9bngCwBI8AdaqxCJa8D8qiWOlbL3RZKXQ5kd62yrABLHMYGUAEzVrEjT3EGgYTBXQXm4XDcCAIAjkIPDhSsGiD0T+zYlHbD5sq3IDFrqgsogkaiVhjtI1q6FuwvdLKCOBuGRx4tNQuiOjr6doLmJa4CQUz20D2yJnVIVlII4Db0qPexF8MQcdhxBOjIsjwPf3pomi9dPE0zLFe7SmPdA3NIqxxIppcVFuYxeGvlUW5jDwEUDLMXKZcxCjciqe5dY7k0OKB0Wb49eEmqHrXiS+GcRoCp/4h+dTMpqJ0rhybF0ccjEeYEj6UhrsXoy+zWLWp+BR7KBUgVC6BtH9ntSCDB0Oh+I1P7JqQ32JmoltJoRugeNMGM4aCduftxp0KyXFsmM0xvEwD5gRNBudnsG18dPnTBcQj45/wAX/TTRZG4M/r5U6FaEbNwp1owZInzNecHht+uNVtrFY5mhcOI+895UA8/iJ34CltBs2F/p0sip2dsACAQJK+QNUV+zJJ38fyFCu9I9nCtL3DutrO6g+LlQPcLUi7eURMA8OZ9Bv7UOIKRR38Bis3cxip4NbDH/ADD5CrLo3D3VX95fF0+CBfxNUnSXVNbzl0xGItFjJCscsnchTqKPhurV23ljF34WfHNMfFmkcOWkmIqqRLZdXMMtzS5bVgCCARMEbHznjTMb0TYuks9skk5viYanjoRXreMZrnZKjrKli5U5YBAhTxbWYPInWIq2tJpxPt+VAEbC4VVUKqwo4Cf61MtwNNfPlSgDkaettRwPrP50go9cwyPowDeaz9agXurmEP8A5e3PNVVG4/aEHiePGoPWDoPtmUpiLtm5lgFQGWOGZTqOO0carsJ0D0pbJjHpcEd0NbVRPNiAWjwBHnQkIl3Oq9lSStu4m+ovXD7SGnw+lQ+irCA3Oxx18sil2V7mYqogHu5UMSR71pOhmu5ct5lNwb5FZV8Yzb/OpOrMYCx8LZlEkQDpxjz3qhFMLmMyzbxlo8s6wPUsWNRH6O6RYy+G6PuMd3OaWPP/AGVaPD9C2Axuph7AaYLi0gad9SBOtTgp5/KlwMpHxLc/ahNcootUpw9SXQAXKdNE7AUnZ0wEVaIEpMyjc0J8X90TSAORUPpPpZbFvN2Fy+5JARNojdjvrtpTbjsRJOnIEE+01O6GxaWmlrYeY+IaiOWulLbZSa8kPE9NYyziHw1ro2wyW4/e3W7NTmUPMkfxRCyZBpcT0r2iQ9i2l0j/AHLEqDyMgZhWj6ydI2roAFsEwO8QJE8PKsvct/6D8qrZyClx0Rlc8d/PapdnDg6kSfI/WmWra/05+o1A8iN6lIP1J/E1VEBUtDy9DSOsahT8gPU604HxP68KW9cAEkhRO5MT4ePlQFFX0v0pbwydpdMAnKBHHfjPLxPhVOf7RMGuhkeQkfJK017s7ilXUMp0IKkqfNWEGqu31VwStnTDgNwOXbyGYgUCYbBdYcPdy5TBYSAylSQeMEAx4gRUxozbanSotnoSwrB+zlwZBaWIOuoJJg6napZwzEgTlWNxueYnhw28aGCsJ2J5GnJYbh9DUixh1HAk+/vrRlQchSSGBa1/qSP9afm0HHx+VEfb8KELY4cd6YqKPFddsHbco10AqYOo3G4iZ+VSujumbOKzCzdByiWKlO6OBPEVG6W6nYHFnPcSHP21JUnTckaNw3Bpj9Tra4UYOzca1aJzXCCpe8f/AHGMaeAA0EbTILksuhOwIdrV0XJjM0yZE7+flwqD1ntdI6NgzbYAa22JBJk6hgQDPIkRFE6rdULWDLNbuXHLCO8ykKCZIVQNNhz2q8xCuF7kTMEkbDiQOJ2+vhR5DwYKz010tbRmvYaWAOVEV223lg7LrrAg/Sbjqv1nxOIcLdwN61O7MpCj+YhfbL61oFsnQM7Enxj6QKNdw4ZSpOhBB22OlFiC4nFm3auNlLQswNyQdAP4jsBxJFMt4tyAezjwLiR5whqsxvV21dCZrl4dmVZQHMAr8OhkD0irNFIAGZT4ldT5wQJ8gKKArrmMXMUQF2G+XZf7zHQeW/hSlX45V92+elDwrZFCqsAeO54k8yedCxJZuMeVZmgl+8y7P8tKEmIZh3tPLj4+FOKCJj1PH8KVQOX4f1NAxotzwp5tTT0J5D2n6zT2ukfe9IH40wArZrwta09MUCcuoPJh9J0PpXmI2OnIjQetUmJobfxIEAn03J4bfoUI3J+z/iMe4H50OxYIknVp1PE/kKb+zs7E3IKgyq65QNYMAjWNyeZqhck2yR/7fo0/8xNEgcMvufxah214KPQCaW4Y0O/Lc+3D1ikFDix8vTT8xUZLEks2ra6nWByHhTyxAJYjmZOg8z8qSwTE5dJkBtDGVV1G4Jyz4SAdQRQBhOs/WjHWrxtW7LLrCtDEMOaldW08fQUzDdO40W2vX7iwpjIqgmdPickxx08NxXSFI4rI8D+BB+tHtWLf3SPILTslowPVDrBjr9wBrLdnxuZSEjlrx/uyfIVvGYAFjr4czwA8TUnshwYfzAj+lB7GG72/A+HHLy4THhQ3YJUPR+dOzefsPzpvZEkAGNdSImPCdAfH9B6LBMExwkmfXWlQ7FIB5+wHz1oF7DswjcHcDiPHifLQHjUnMf8AXWkJHl/XamAKzajn+J9aOnlPMwQJ9TqPH5V4OZ70n2n+tEEcD7iP6fOkI9kB4CkKciR9Panx417LTAj52XcZh4DX24+ketS7TKQCDIOoOtDyRQACGMaLw8SdSfc7UCJb25pos+FMYzzLE7cOJmeA0obmDGQn0pAZDonrRYugQSGP2TE/ynZvSrdLgaI25fr9aVwCXU906cuFarqz17v2CqXMt1JAhzDDyu/9U+YqdpbZ1c66nhsOX9aVQOO363qN0V0nZxI/ct3gJa0/duJPMcR4iR41MOF8NfAj86TGmee4BSiyx+77n8q8LZHH3ZfxM0x7Y4t6CWP4D50IYG4QDwJHI6Dhvz1NOVSYY6DhzJ/KmEj7A/maD7DYfOmHzJPMmTTESTd2zlSeeob3E/OmMV4FgfIH5yPpQAlFVaoKBk6wQzL4GD/hOnzo5QKAQpM6DXjygAa14kDh7flSu4XX6caBUefDgxO418uGnAHfUa0TswIgfKQNeXE/rwLLFtxM695iDOpVjnA8CuYr4gDxiZb5fLYihiQ20GzaFgvoCfbSpMH7x968i+Ip/qPnQOgNxysTqJA8dSBPuR+hB9cXhJHl+oozR+vwFMce/AfnQIEeRYA8+B/Ly1p6ow8fnTAQIPpJ1r1/FqkZ7oSdpYAnyG5oAfNOCHlUP/tK1P8Ath/xflUmwc2qvm5w2b5Tp6inQrFvNlBJ1gExxMDbwoGFVmGa4deQ0UeEcfWaKyx9kEecH8j8vOnJHiPA6HT/AFGokUgHBR935UTTiPkPzpmGUiR4kj1JJ9ifajGgBguLzjz0H5U+ecEeG/pwoF1RxqmxWMNolrZJAElYkEcdOflr9CxMvyY21H08xwpAR+o/Og4a4GVXGmZQw9QDRpHjQB82sRQXszRVhhoaUHnWfRp32Lh8TcTLDkBTKme8n91t19DWv6A663c4S8c44NoH9eDfI+dY8imZJNNSDbXR3fB9I23WQQeccPMbinXrgIJG36/XrXF8H0xet6BiRwP2l8m/AzWy6u9dRHZ4hZ0+NAJ82TY+a+1VQmzZMdKHYuZh4qSrDlqYPkRB9aXD3EuLmtsHXmuseBG4PgaREGbMNG2njHLy8KQwyinK8nKNzx4etFt3P4R5gkT50ZBOyj0FAxn7Ll7zsDHLQf1pLduToPLwoxwxJljHhx9qbnnupoN54kcxyH18qCQlzLtO35abUdbp4jN/eA+u9R9EFOR2PCPPX6HT3NMVUHzfwj3NOW4OK/P8KGCefyH5U8PHAfT9e1ADzP2co9IPvQSCJnl8p1/Cihgdv6jx8vKhPeIkASSDAOgPMeBI+tADLtyFdlEuqsVHNgCQPeuDYjrRiDca6rDM5JlgGOvEzpO3gK7vYbSVBjjp3lPJ13B/121rD9b/AOzxMQzXsMwt3G1ZT/s3PEiNUY8YkHkNTTi6FJXycvPWLF5y/bvJ3g930X4R6Ctb1X6XxXZNiL11Si6W1IGYsTGbMIKqIbXXbaqmx1Dxi3QL1lhbGrMsMCAdlKzBPlpvGlG6TfEktbS1cCiFVFRoGWQCsCeJMjnTsmjoPVTrxbxHdYnxzfGuwzE/aSSBJ1E+lbVl4VxPqb1KxjX7V24hsW0YMS4h2E6qqHXUaSYEHjtXaWeASeNKTHFMUfTceexHh/WnDy9qDcuAMAeCHMOOpGT6P7Gnp7eX4k0gPPB0mkt5QI+LxME0pusNhPzpvankPaKB0Lv9NNgKb+1oPvHxCOw9CBBpxCt8Sz6z8jXjaT7z0CZ8x3gVaRpIB9wCfnNS8HdL6EaxOnEDUmPACm310XTYR7Gfxp9jCturBdN+EeO9D6KXLCvbI/KkWvW7ssqzJiIYZdvhjXciAJ+lShYLKHykKZCkgiSujAeVQ0i+UIFpMv6+f1ApyNzpWIqbaZdKSJHQ/Sd202YMwI2Zd/IjZh5ztW96J6923GXEKAfvqsr/ADJqV8xPpXPLAp16xp3dDVrJfZm8ddHa8JjLbgMpUqdmUKQfI61YQY+I+h/KuIdCdKXcMTqYO5X/AJkOhrb9GddbUgOwUHTMJKT/ABDdD5+sU+w67NlbJVSJ1YhT5Zhm8jln5UxFlifQfjS2nzpmSGmGUqQVbKQYB21iJ8aIg4jVW1B/A8jPCh9Ci1YIr3gTtHzJM/Qe1SA9KT4Ui2+TDyOh/KgZ4vSoWbRVJpTZbkP8Q/OktLkmGkn2oBuuhveUrKkEtEeBBzA+gJ8wKZiNvUR5zRcRibjRLbcY2HIew/WlRkdRLsYRBMnYeNJ+wL3ZKuMAZ1kRqN4M6eI8DpSgq3gfDT3FQsNiC0nLBYyZ+yNAFP8AFAEjYHNrUnJVGaCnD+IPypi67EHyYfnQxbWm9kZkH3oGSOxPgK8VjWJPNtAPTc/rWhrdI3cesURgpGoI8RqKAtg2Qb7zBJ5zx8or2UyI9fGjqoyiDIiD5c6HOviP1NJggtlWuZiDlRWKqNi2XRiTuBmkQPuneREW27zBJWOG/wA5qSBKnIYOp9SZPzn3oKLx402wih5ZuYPmJ+tJ2n8HsdP81LSTQNnz1i7PcY5QwnRhIK6QQRrM+PoeFRylwDSdojUQBp6+dWCORqP9fA0l21mByEBo1Vo13+A+u3zqbKKn9lVgp7QBjuDuDP6M1Y3Ma4tqruXKiF3gAkmIPiza+dRbaFD8EHx0PpIPyijXHzE6bjWeUSSf1zoasqMtoOzjhrmHgNPejBDGcEGZEAieGpHAfkarcRE1607LqNvl6iqogucM+tSTVdhL6Nvox0E7eh0o7sy6VlLH7Gkcnhkqaj4i3oSo1NeS7PnTg2tTG4stpSRbdWum8Rh27j5OJEgo3mh0J8teVdC6M61K0G6gtFjBOpsu397U229xz4EcrmpWHuvbVyhjMO8IBDRtIO9bLIn2YSxVyjta3UJAzBSdQrkCRwKNOVx4qTRmssN1Ncl6v9bGtgqCFXU9ldE2H55SfgbzI8ztW36H6fwV6F1w9w/Yzsin+4ykKfIgHwq9qI3M0JTwNeFpuUDmajnDg6dpe/8Ayv8AnSf9l2jqy5/77O/yYkUqQ9z9ht3G2gYUm8/3bcEDzb4V9TUe9ZdypuFQZ7ltfhtxrnY/bcRoYgEiBxq0VABAgDgAIHyqJcWGH91/8yUuPAnbCYa2AP1tTmbbx2H1PgP1ynynSgjV2HAW0j1L5/onyoALm5flTAx+8fc/nRKHcoHQQOeMEeIn+vzpyEfZMeBOh8AefgY8JoCmvEx+XOiwaCkEGV0PEc/yNRrt8famBsQNU8HH3P4uA30E0UXNhMg/AeO05Tz0kg+BnYSiyhB3k60AERSsAyDwPPyPGnXBOux5jY+YqQTI8D6g/wBf1woVtM2xAPIn6GigsaJ5T4jX+tJPn7GldWXcEeVDOKPP5UDOCW1kwuw5kE76bRJiOFeYU63b03nNqf8AERv6b+NEuwREajSfwoaEmD7QEENy34+E8xUDFDLud/n5VKYUtkjY6jlUop8kDD2wTryJ9BUh7WfUiOQ/Oi3FCklQSAdzExypquSe7BB1HAxr/X2qyCqugTpUi1iysK2o+Ypt22Dcyr8ufGm4i0ZH6JooCwW4G1Un8fbhTxcqpRmXUSP186ssFmuAmPh3I2109KlqylJrokK1WWGMjnVQykfjVhgrvDY8jWU4Nco2hNPhk/KIiKi3bB4HT7p29OVGD15nrKM3FmkoJkroXrHesOLbMGT7KOdR4K+/pt4V0XorptLmitDfcbf05+lcqu4VGMsJ0jWi2L9y1GViyjZWM+k7xW/zEzDY0doW/O+lCdtQfHXyP9YPkKwvR/W3SJzc1bRx5H7Xz4bVo+r3S9rEk9m4YjRkOjDzXiPESKtEOi5FCYkEMBMSCPvKfiA8dAR5RpNSDbPr9R+Y/rxMNiaYrs8CBBBlT8J5/kaeyzQ07s8juOBPP+E+PuDpTxbH2Wjwbb32/W1DBMHk1IqNlLPkmNJFS2wzzw89Yry4Ihs061PZVi4jDhLW8le9P8SnN9RFBxl3v5Qdj9CalsxEBuYJ8SNRPhMH0FVeLCs4uKwMyCBvPMjeql0RHllhYJIIG4Mjz3HpQsWoJDrPeHDT3p/R40J8qrcTijcuJh0JGVFuXmGhVDoltTwdyG13Cq0QSpCXKG3TLfD3nA1YHz/W9ebEW51A/XrUEHNoNFGgA0ED8PCnxTCji6EqigHSZIOoJGokbGMx9zQws8oE8ANdN433G9er1UIMbX7srA1J1O4gcP8AF8qgMoB024eXClr1SxoWKVcOCrZAFaJJkwdY29aSvUkMprN3IGjc6a/qa8LsTOpr1eqyTzPIiN6TB3mRgR7HUe1LXqQFrc6RXsz3TmBAPI68/IHnR1hwGGxE/nXq9SGEt3DGutPS/Xq9WeSK7NMcn0GzUuevV6uY3FCgkGNRqPMbVVti2XEM2xzSCndKneVilr1dWFumc2VHROh+vN23lt4pe1WFIuLpcWQCJ2DHUcjvqa3/AGWbUaHKG8wdpHA/rwpK9WzRigIfgaWOWler1QWNW6w+77a079qbwr1epWVRGva71CuLDCOOlLXqllInq3dC89PkST7A+sVT9BGWxtw7tibieS2Ut21HyJ9a9Xq0XRl5LK0NKQmvV6kWf//Z" alt="Plasma CNC Cutting" style="object-fit: contain;">
                        </div>
                        <div class="p-6">
                            <h4 class="font-bold text-xl text-slate-900 mb-2">Plasma CNC Cutting</h4>
                            <p class="text-slate-600 mb-4">High-precision automated cutting service</p>
                            <div class="flex gap-3">
                                <button onclick="updateProduct('plasma')" class="flex-1 py-2.5 bg-blue-600 text-white rounded-lg font-medium hover:bg-blue-700 transition text-sm">
                                    <i class="fas fa-info-circle mr-2"></i>View Details
                                </button>
                                <button onclick="openOrderModalWithProduct('plasma')" class="flex-1 py-2.5 bg-slate-200 text-slate-700 rounded-lg font-medium hover:bg-slate-300 transition text-sm">
                                    <i class="fas fa-shopping-cart mr-2"></i>Order
                                </button>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="text-center mt-16">
                    <button onclick="showAllProducts()" class="px-8 py-3.5 bg-gradient-to-r from-blue-600 to-blue-800 text-white font-bold rounded-xl hover:from-blue-700 hover:to-blue-900 transition shadow-lg">
                        <i class="fas fa-boxes mr-2"></i>View All Products Catalog
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
                        <a href="tel:+919123456789" class="text-blue-700 font-bold text-lg hover:text-blue-800">+91 7307709671</a>
                        <p class="text-slate-500 text-sm mt-2">Mon-Fri, 8:00 AM - 6:00 PM IST</p>
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
                            india maharashtra
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
                            <li><a href="#" onclick="updateProduct('lwn'); return false;" class="hover:text-white transition">Long Weld Neck Flanges</a></li>
                            <li><a href="#" onclick="updateProduct('wnf'); return false;" class="hover:text-white transition">Weld Neck Flanges</a></li>
                            <li><a href="#" onclick="updateProduct('slipon'); return false;" class="hover:text-white transition">Slip-On Flanges</a></li>
                            <li><a href="#" onclick="updateProduct('blind'); return false;" class="hover:text-white transition">Blind Flanges</a></li>
                            <li><a href="#" onclick="updateProduct('plasma'); return false;" class="hover:text-white transition">Plasma CNC Cutting</a></li>
                        </ul>
                    </div>
                    
                    <div>
                        <h4 class="font-bold text-lg mb-6">Resources</h4>
                        <ul class="space-y-3 text-slate-400">
                            <li><a href="#" onclick="document.getElementById('specifications').scrollIntoView({behavior:'smooth'}); return false;" class="hover:text-white transition">Technical Specifications</a></li>
                            <li><a href="#" onclick="downloadProductFiles(); return false;" class="hover:text-white transition">CAD Drawings</a></li>
                            <li><a href="#" onclick="document.getElementById('about').scrollIntoView({behavior:'smooth'}); return false;" class="hover:text-white transition">Material Selection Guide</a></li>
                            <li><a href="#" class="hover:text-white transition">Installation Manuals</a></li>
                            <li><a href="#" onclick="showAllProducts(); return false;" class="hover:text-white transition">Product Catalog</a></li>
                        </ul>
                    </div>
                    
                    <div>
                        <h4 class="font-bold text-lg mb-6">Ordering Process</h4>
                        <ul class="space-y-3 text-slate-400">
                            <li><a href="#" onclick="openOrderModal(); return false;" class="hover:text-white transition">Request Quotation</a></li>
                            <li><a href="#" class="hover:text-white transition">Pricing & Delivery</a></li>
                            <li><a href="#" class="hover:text-white transition">Payment Terms</a></li>
                            <li><a href="#" class="hover:text-white transition">Order Tracking</a></li>
                            <li><a href="#" onclick="openDashboard(); return false;" class="hover:text-white transition">Supplier Portal</a></li>
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
        // Global Variables
        let currentUserType = 'partner';
        let isSupplier = false; // Track if user is a supplier
        
        // Enhanced Authentication Management
        function toggleAuthView(view) {
            document.getElementById('login-form').classList.toggle('hidden', view !== 'login');
            document.getElementById('signup-form').classList.toggle('hidden', view !== 'signup');
        }
        
        function closeAuth() {
            document.getElementById('auth-overlay').classList.add('hidden');
        }

        function setUserType(type) {
            currentUserType = type;
            const buttons = document.querySelectorAll('#login-form button[onclick^="setUserType"]');
            buttons.forEach(btn => {
                if (btn.textContent.includes(type === 'partner' ? 'Partner' : 'Supplier')) {
                    btn.classList.add('border-blue-200', 'bg-blue-50', 'text-blue-700');
                    btn.classList.remove('border-slate-200', 'hover:border-blue-200', 'hover:bg-blue-50');
                } else {
                    btn.classList.remove('border-blue-200', 'bg-blue-50', 'text-blue-700');
                    btn.classList.add('border-slate-200', 'hover:border-blue-200', 'hover:bg-blue-50');
                }
            });
        }

        function handleAuth(event, userType) {
            if (event) event.preventDefault();
            const loader = document.getElementById('transition-loader');
            loader.style.left = '0%';
            
            setTimeout(() => {
                const statusBadge = document.getElementById('user-status');
                const mobileStatus = document.getElementById('mobile-user-status');
                
                // Reset supplier flag
                isSupplier = false;
                
                if (userType === 'visitor') {
                    statusBadge.innerText = 'Visitor Mode';
                    statusBadge.className = 'px-3 py-1.5 bg-blue-50 rounded-full text-xs font-bold text-blue-600 uppercase border border-blue-100';
                    statusBadge.innerHTML = '<i class="fas fa-user mr-1"></i>Visitor';
                    
                    mobileStatus.innerText = 'Visitor Mode';
                    mobileStatus.className = 'px-3 py-2 bg-blue-50 rounded-lg text-sm font-bold text-blue-600';
                } else if (userType === 'supplier' || currentUserType === 'supplier') {
                    // Set supplier flag
                    isSupplier = true;
                    
                    statusBadge.innerText = 'Supplier';
                    statusBadge.className = 'px-3 py-1.5 bg-green-50 rounded-full text-xs font-bold text-green-600 uppercase border border-green-100';
                    statusBadge.innerHTML = '<i class="fas fa-building mr-1"></i>Supplier';
                    
                    mobileStatus.innerText = 'Supplier';
                    mobileStatus.className = 'px-3 py-2 bg-green-50 rounded-lg text-sm font-bold text-green-600';
                    
                    // Add dashboard button to desktop navigation for suppliers only
                    addDashboardButtonToNav();
                    
                    // Add dashboard button to mobile menu for suppliers only
                    addDashboardButtonToMobileMenu();
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
                updateProduct('lwn');
                
                if (isSupplier) {
                    setTimeout(() => {
                        showNotification('Welcome to Supplier Dashboard! Access your business analytics and manage orders.', 'success');
                    }, 500);
                }
            }, 1000);
        }

        function addDashboardButtonToNav() {
            const navActions = document.querySelector('.hidden.lg\\:flex.space-x-8.font-medium.text-sm.items-center > .flex.items-center.gap-4');
            if (!navActions) return;
            
            // Remove existing dashboard button if any
            const existingDashboardBtn = navActions.querySelector('button[onclick="openDashboard()"]');
            if (existingDashboardBtn) {
                existingDashboardBtn.remove();
            }
            
            // Add dashboard button before logout button
            const logoutBtn = navActions.querySelector('button[onclick="logout()"]');
            if (logoutBtn) {
                const dashboardBtn = document.createElement('button');
                dashboardBtn.innerHTML = '<i class="fas fa-chart-bar mr-1"></i>Dashboard';
                dashboardBtn.className = 'px-4 py-2 bg-slate-100 text-slate-700 rounded-lg font-medium hover:bg-slate-200 transition flex items-center gap-2 text-sm';
                dashboardBtn.onclick = openDashboard;
                navActions.insertBefore(dashboardBtn, logoutBtn);
            }
        }

        function addDashboardButtonToMobileMenu() {
            const mobileMenuActions = document.querySelector('#mobile-menu .space-y-2');
            if (!mobileMenuActions) return;
            
            // Remove existing dashboard button if any
            const existingDashboardBtn = mobileMenuActions.querySelector('button[onclick="openDashboard()"]');
            if (existingDashboardBtn) {
                existingDashboardBtn.remove();
            }
            
            // Add dashboard button before logout button
            const logoutBtn = mobileMenuActions.querySelector('button[onclick="logout()"]');
            if (logoutBtn) {
                const dashboardBtn = document.createElement('button');
                dashboardBtn.innerHTML = '<i class="fas fa-chart-bar"></i> Supplier Dashboard';
                dashboardBtn.className = 'w-full text-left text-blue-600 hover:text-blue-800 font-medium py-2 flex items-center gap-2';
                dashboardBtn.onclick = openDashboard;
                mobileMenuActions.insertBefore(dashboardBtn, logoutBtn);
            }
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
                closeDashboard();
                isSupplier = false;
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

        // Dashboard Functions - Only for Supplier Accounts
        function openDashboard() {
            // Check if user is a supplier
            if (!isSupplier) {
                showNotification('Dashboard access is only available for supplier accounts.', 'error');
                return;
            }
            
            document.getElementById('dashboard-modal').classList.remove('hidden');
            document.body.style.overflow = 'hidden';
            initDashboardCharts();
        }
        
        function closeDashboard() {
            document.getElementById('dashboard-modal').classList.add('hidden');
            document.body.style.overflow = 'auto';
        }
        
        function switchDashboardTab(tabName) {
            // Update tab buttons
            document.querySelectorAll('#dashboard-modal .tab-button').forEach(btn => {
                btn.classList.toggle('active', btn.getAttribute('onclick').includes(tabName));
            });
            
            // Show selected tab content
            document.querySelectorAll('#dashboard-modal .tab-content').forEach(content => {
                content.classList.toggle('active', content.id === `dashboard-${tabName}`);
                content.classList.toggle('hidden', content.id !== `dashboard-${tabName}`);
            });
            
            // Initialize charts if needed
            if (tabName === 'analytics') {
                setTimeout(() => {
                    initAnalyticsCharts();
                }, 100);
            }
        }
        
        // Chart Initialization
        function initDashboardCharts() {
            // Sales Chart
            const salesCtx = document.getElementById('salesChart').getContext('2d');
            new Chart(salesCtx, {
                type: 'line',
                data: {
                    labels: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun'],
                    datasets: [{
                        label: 'Revenue (₹)',
                        data: [1200000, 1850000, 1500000, 2200000, 2450000, 2847500],
                        borderColor: '#3b82f6',
                        backgroundColor: 'rgba(59, 130, 246, 0.1)',
                        borderWidth: 2,
                        fill: true,
                        tension: 0.4
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: {
                            display: false
                        }
                    },
                    scales: {
                        y: {
                            beginAtZero: true,
                            ticks: {
                                callback: function(value) {
                                    return '₹' + (value / 1000000).toFixed(1) + 'M';
                                }
                            }
                        }
                    }
                }
            });
        }
        
        function initAnalyticsCharts() {
            // Category Chart
            const categoryCtx = document.getElementById('categoryChart').getContext('2d');
            new Chart(categoryCtx, {
                type: 'doughnut',
                data: {
                    labels: ['Weld Neck', 'Long Weld Neck', 'Blind Flange', 'Plasma CNC', 'Others'],
                    datasets: [{
                        data: [42, 30, 12, 8, 8],
                        backgroundColor: [
                            '#3b82f6',
                            '#10b981',
                            '#f59e0b',
                            '#8b5cf6',
                            '#64748b'
                        ]
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: {
                            position: 'bottom'
                        }
                    }
                }
            });
            
            // Performance Chart
            const performanceCtx = document.getElementById('performanceChart').getContext('2d');
            new Chart(performanceCtx, {
                type: 'bar',
                data: {
                    labels: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun'],
                    datasets: [
                        {
                            label: 'Orders',
                            data: [32, 45, 38, 52, 47, 56],
                            backgroundColor: '#3b82f6'
                        },
                        {
                            label: 'Revenue (₹L)',
                            data: [120, 185, 150, 220, 245, 284],
                            backgroundColor: '#10b981'
                        }
                    ]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: {
                        y: {
                            beginAtZero: true
                        }
                    }
                }
            });
            
            // Conversion Chart
            const conversionCtx = document.getElementById('conversionChart').getContext('2d');
            new Chart(conversionCtx, {
                type: 'doughnut',
                data: {
                    labels: ['Converted', 'Not Converted'],
                    datasets: [{
                        data: [68, 32],
                        backgroundColor: ['#3b82f6', '#e2e8f0']
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    cutout: '70%',
                    plugins: {
                        legend: {
                            display: false
                        }
                    }
                }
            });
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
            console.log('Supplier Phone: +91 7307709671');
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

        // Product Data with image references
        const productData = {
            lwn: {
                title: "Long Weld Neck Flange (LWN)",
                desc: "ASME B16.5 Class 900 DN15 Long Weld Neck flange with extended hub design for pressure vessel applications. Engineered for high-pressure systems where reliability and structural integrity are critical. Manufactured with full traceability and compliance to international standards.",
                features: [
                    "ASME B16.5 Class 900 compliant",
                    "Nominal Diameter: DN15 (1/2\")",
                    "Extended hub for stress distribution",
                    "Full material traceability",
                    "Precision machined sealing surface",
                    "Ideal for pressure vessel connections"
                ],
                image: "long weldneck.png",
                specs: {
                    general: {
                        "Reference": "ASMEB16.5-900-DN15",
                        "Standard": "ASME B16.5",
                        "Nominal Pressure": "150",
                        "Nominal Diameter": "15 mm (1/2\")",
                        "Design": "Flange ASME B16.5 - ASME 900 - Long Weld Neck",
                        "Supplier": "CAMAN",
                        "OmniClass23": "23.27.45.29"
                    },
                    materials: {
                        "Stainless Steel": "ASTM A182 F316/316L, F304/304L",
                        "Carbon Steel": "ASTM A105, A350 LF2",
                        "Alloy Steel": "ASTM A182 F11, F22, F91",
                        "Duplex Steel": "A182 F51 (2205), F53 (2507)",
                        "Special Alloys": "Inconel 625, Monel 400, Hastelloy"
                    }
                }
            },
            wnf: {
                title: "Weld Neck Flange (WNF)",
                desc: "High-performance flanges engineered for severe service conditions, featuring a long tapered hub that reduces stress concentrations and improves fatigue resistance. Ideal for high-pressure, high-temperature, and cryogenic applications.",
                features: [
                    "Designed for high-pressure systems (up to 2500#)",
                    "Long tapered hub reduces stress concentration",
                    "Matches pipe internal diameter for smooth flow",
                    "Certified for high-temperature and cryogenic service",
                    "ASME B16.5 compliant design",
                    "Available with RF, RTJ, or FF faces"
                ],
                image: "weld neck.png",
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
            slipon: {
                title: "Slip-On Flange",
                desc: "A cost-effective flange solution that slides over the pipe and is welded both inside and outside for strength. Easier to align than weld neck flanges and suitable for lower pressure applications.",
                features: [
                    "Lower installation cost and time",
                    "Easy alignment during installation",
                    "Suitable for standard pressure duty",
                    "Internal and external welding for strength",
                    "Available in raised face or flat face"
                ],
                image: "slip on flange.png",
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
                features: [
                    "Pressure isolation and system closure",
                    "Removable for maintenance access",
                    "Solid forged construction for strength",
                    "Critical safety shut-off component",
                    "Available with or without jack screw holes"
                ],
                image: "blind.png",
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
                features: [
                    "Waterproofing for pipe penetrations",
                    "Cast iron or fabricated construction",
                    "Civil engineering standard compliance",
                    "Watertight seal with concrete",
                    "Available with or without anchoring studs"
                ],
                image: "puddle flange.png",
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
                features: [
                    "Cutting capacity up to 100mm thickness",
                    "Complex CAD geometry translation",
                    "Fast turnaround (3-5 business days)",
                    "Superior edge finish with minimal dross",
                    "Nesting optimization for material efficiency"
                ],
                image: "plasma cutting.png",
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
                features: [
                    "Extreme thickness capability (300mm+)",
                    "Structural integrity preservation",
                    "Massive scale capacity",
                    "Precision oxy-fuel technology",
                    "Straightness within 1mm per meter"
                ],
                image: "images/profile-cutting.jpg",
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

        // Product Functions
        function downloadProductFiles() {
            const currentProduct = getCurrentProduct();
            if (currentProduct && currentProduct.title) {
                showNotification(`Preparing ${currentProduct.title} technical files for download...`, 'info');
                setTimeout(() => {
                    showNotification(`${currentProduct.title} technical files ready for download`, 'success');
                    const link = document.createElement('a');
                    link.href = '#';
                    link.download = `${currentProduct.title.replace(/\s+/g, '_')}_technical_specs.pdf`;
                    link.click();
                }, 1500);
            }
        }

        function requestCustomQuote() {
            openOrderModal();
            showNotification('Custom quote request form opened', 'info');
        }

        function showAllProducts() {
            document.getElementById('product-gallery').scrollIntoView({ 
                behavior: 'smooth',
                block: 'start'
            });
            showNotification('Viewing all products gallery', 'info');
        }

        function showNotification(message, type = 'info') {
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
            return productData.lwn;
        }

        function updateProduct(key) {
            const data = productData[key] || productData.lwn;
            
            // Update active chip
            document.querySelectorAll('.flange-chip').forEach(c => c.classList.remove('active'));
            const activeChip = document.getElementById(`chip-${key}`);
            if (activeChip) activeChip.classList.add('active');

            // Update product image
            const productImage = document.getElementById('product-main-image');
            if (data.image && productImage) {
                productImage.src = data.image;
                productImage.alt = data.title;
            }

            // Update product info
            document.getElementById('current-product-name').textContent = data.title;

            // Update product details
            document.getElementById('p-title').innerText = data.title;
            document.getElementById('p-desc').innerText = data.desc;
            
            // Update features
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
                initReveal();
                
                document.getElementById('products').scrollIntoView({ 
                    behavior: 'smooth',
                    block: 'start'
                });
            }, 50);
            
            showNotification(`Loaded ${data.title} details`, 'success');
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

        // Initialize
        window.onload = () => {
            setUserType('partner');
            updateProduct('lwn');
            initReveal();
            
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
            
            // Close modals on escape key
            document.addEventListener('keydown', (e) => {
                if (e.key === 'Escape') {
                    const orderModal = document.getElementById('order-modal');
                    if (orderModal && !orderModal.classList.contains('hidden')) {
                        closeOrderModal();
                    }
                    const dashboardModal = document.getElementById('dashboard-modal');
                    if (dashboardModal && !dashboardModal.classList.contains('hidden')) {
                        closeDashboard();
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
        };
    </script>
</body>
</html>
