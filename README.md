# cali_house_data_lin_reg

╔═══════════════════════════════════════════════════════════════════════════════════╗
║                    CALIFORNIA HOUSING LINEAR REGRESSION ANALYSIS                 ║
║                                    FLOWCHART                                     ║
╚═══════════════════════════════════════════════════════════════════════════════════╝

┌─────────────────────────────────────┐
│     📊 LOAD DATASET                 │
│  • California Housing Data          │
│  • Shape: (20,640 × 9)             │
│  • Target: MedHouseVal              │
└─────────────────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────────┐
│   🔍 EXPLORATORY DATA ANALYSIS      │
│  • df.describe()                    │
│  • Correlation Matrix               │
│  • Heatmap Visualization            │
│  • Pairplot Analysis                │
└─────────────────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────────┐
│    ⚙️ DATA PREPROCESSING            │
│  • Train-Test Split (80/20)         │
│  • X = features, y = target         │
│  • StandardScaler normalization     │
│  • X_train_scaled, X_test_scaled    │
└─────────────────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────────┐
│   🤖 BASELINE LINEAR REGRESSION     │
│  • Fit on all original features     │
│  • LinearRegression()               │
│  • Predict on test set              │
└─────────────────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────────┐
│      📊 BASELINE PERFORMANCE        │
│  • RMSE: 0.746                     │
│  • MAE:  0.533                     │
│  • R²:   0.576                     │
└─────────────────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────────┐
│   🎯 FEATURE SELECTION (RFE)        │
│  • Recursive Feature Elimination    │
│  • Select top 5 features            │
│  • RFE(LinearRegression(), n=5)     │
└─────────────────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────────┐
│      ✅ SELECTED FEATURES           │
│  1. MedInc                          │
│  2. AveRooms                        │
│  3. AveBedrms                       │
│  4. Latitude                        │
│  5. Longitude                       │
└─────────────────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────────┐
│     🔧 FEATURE ENGINEERING          │
│  • RoomsPerPerson = AveRooms/       │
│    AveOccup                         │
│  • BedroomsPerRoom = AveBedrms/     │
│    AveRooms                         │
└─────────────────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────────┐
│  🏆 FINAL MODEL TRAINING            │
│  • LinearRegression on selected     │
│    features                         │
│  • Fit and predict                  │
└─────────────────────────────────────┘
                 │
                 ▼
╔═════════════════════════════════════════════════════════════════════════════════╗
║                              📐 FINAL MODEL EQUATION                           ║
║                                                                                 ║
║  ŷ = 2.072 + 0.832×MedInc - 0.299×AveRooms + 0.339×AveBedrms                 ║
║              - 0.985×Latitude - 0.964×Longitude                                ║
╚═════════════════════════════════════════════════════════════════════════════════╝
                 │
                 ▼
┌─────────────────────────────────────┐
│    📈 FEATURE SELECTION RESULTS     │
│  • RMSE: 0.753                     │
│  • MAE:  0.539                     │
│  • R²:   0.567                     │
└─────────────────────────────────────┘
                 │
                 ▼
╔═════════════════════════════════════════════════════════════════════════════════╗
║                            🔍 COEFFICIENT INTERPRETATION                       ║
╠═════════════════════════════════════════════════════════════════════════════════╣
║  Feature      │ Coefficient │ Impact                                            ║
║───────────────┼─────────────┼───────────────────────────────────────────────────║
║  MedInc       │   +0.832    │ Higher income ────────────> Higher house value   ║
║  AveRooms     │   -0.299    │ More rooms ───────────────> Slightly lower value ║
║  AveBedrms    │   +0.339    │ More bedrooms ────────────> Higher house value   ║
║  Latitude     │   -0.985    │ Higher latitude ──────────> Lower house value    ║
║  Longitude    │   -0.964    │ Higher longitude ─────────> Lower house value    ║
╚═════════════════════════════════════════════════════════════════════════════════╝
                 │
                 ▼
┌─────────────────────────────────────┐
│    📊 COEFFICIENT VISUALIZATION     │
│  • Bar plot of coefficients         │
│  • Green bars: positive impact      │
│  • Red bars: negative impact        │
└─────────────────────────────────────┘
                 │
                 ▼
╔═════════════════════════════════════════════════════════════════════════════════╗
║                           📋 MODEL COMPARISON TABLE                            ║
╠═════════════════════════════════════════════════════════════════════════════════╣
║  Model Type               │  RMSE  │  MAE   │   R²   │                         ║
║───────────────────────────┼────────┼────────┼────────┼─────────────────────────║
║  Baseline (All Features)  │ 0.746  │ 0.533  │ 0.576  │ ←── Original Model      ║
║  Selected Features (5)    │ 0.753  │ 0.539  │ 0.567  │ ←── Optimized Model     ║
╚═════════════════════════════════════════════════════════════════════════════════╝
                 │
                 ▼
┌─────────────────────────────────────┐
│   🎯 PREDICTION SYSTEM SETUP        │
│  • User input collection            │
│  • Feature scaling                  │
│  • Model prediction                 │
│  • Output: House value in $100k     │
└─────────────────────────────────────┘
                 │
                 ▼
╔═════════════════════════════════════════════════════════════════════════════════╗
║                              🎊 KEY INSIGHTS & RESULTS                        ║
╠═════════════════════════════════════════════════════════════════════════════════╣
║                                                                                 ║
║  ✓ Feature selection maintains 95%+ of original model performance              ║
║                                                                                 ║
║  ✓ MedInc (Median Income) has strongest positive impact on house prices        ║
║                                                                                 ║
║  ✓ Geographic location (Lat/Long) strongly affects pricing                     ║
║                                                                                 ║
║  ✓ Model is interpretable and suitable for price estimation                    ║
║                                                                                 ║
║  ✓ Simplified 5-feature model reduces complexity while maintaining accuracy    ║
║                                                                                 ║
║  ⚠️ Predictions should be interpreted within training data range               ║
║                                                                                 ║
╚═════════════════════════════════════════════════════════════════════════════════╝

╔═════════════════════════════════════════════════════════════════════════════════╗
║                                 🏁 END OF ANALYSIS                            ║
╚═════════════════════════════════════════════════════════════════════════════════╝
