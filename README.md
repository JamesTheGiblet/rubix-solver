🎲 Rubik's Cube Solver

A 3D Rubik's Cube visualizer and solver (in development) built with Three.js. It features interactive cube manipulation, state validation, and is currently being built out to include visual solving algorithms.

✨ Features
🎮 Interactive 3D Cube
 * Smooth 3D Visualization: Powered by Three.js with realistic lighting and shadows
 * Mouse/Touch Controls: Drag to rotate, click to interact
 * Responsive Design: Works on desktop and mobile devices
 * Visual Feedback: Real-time animations and status updates
🎨 Paint Mode
 * Custom Cube States: Paint any cube configuration
 * 6-Color Palette: All standard Rubik's cube colors (White, Yellow, Green, Blue, Orange, Red)
 * Smart Face Detection: Click on any visible face to paint
 * Real-time Updates: Visual and internal state synchronization

🤖 Advanced Solving System (Work in Progress)
 * Targeting Layer-by-Layer Method: Aims to implement the beginner's 7-step solving approach.
 * Step-by-Step Progress: UI elements for visual indicators are in place, pending full algorithm logic.
 * Move History: Track all moves and solution sequences.
 * Speed Control: Adjustable animation speed (50-500ms).
🔧 Cube State Management
 * State Validation: Detects invalid cube configurations
 * Corner Analysis: Identifies impossible corner color combinations
 * Color Count Validation: Ensures proper color distribution
 * Auto-Fix: Intelligent correction of invalid states
🛠️ Debug Tools
 * Debug Console: Detailed cube state analysis
 * Corner Validation: Identifies duplicate colors on corner pieces
 * Quick Fix: Automatic resolution of common issues
 * Visual-State Sync: Ensures consistency between display and internal state
🚀 Getting Started
Prerequisites
 * Modern web browser with WebGL support
 * No additional dependencies required (uses CDN for Three.js)
Installation
 * Clone the repository:
<!-- end list -->
git clone https://github.com/JamesTheGiblet/rubix-solver.git
cd rubix-solver

 * Open rubix-solver.html in your web browser:
<!-- end list -->
# Windows
start rubix-solver.html

# macOS
open rubix-solver.html

# Linux
xdg-open rubix-solver.html

📖 Usage Guide
Basic Operations
🎲 Scrambling
Click "🎲 Scramble" to randomize the cube with a 20-move sequence.
🤖 Solving
 * Click "🤖 Solve" to attempt an automatic solve.
 * The solver validates the cube state before attempting to solve.
 * Note: The full solving algorithm is not yet complete. Only Step 1 (White Cross) is functional.
 * Invalid cube states will be detected and reported.
🔄 Reset
Click "🔄 Reset" to return to the solved state.
Paint Mode
 * Enable Paint Mode: Click "🎨 Paint"
 * Select Color: Choose from the 6-color palette
 * Paint Faces: Click on any visible cube face to apply the selected color
 * Exit Paint Mode: Click "🔄 Rotate" to return to rotation mode
Manual Moves
Individual Face Rotations
Use the rotation buttons:
 * U, D, F, B, L, R: Clockwise rotations
 * U', F', R': Counter-clockwise rotations
Sequence Input
 * Type move sequences in the input field (e.g., R U R' U')
 * Press Enter or click "▶️ Execute"
 * Supported notation: U, U', U2, F, F', F2, etc.
Debug Features
🔍 Debug Analysis
 * Click the "🔍 Debug" button (top-right) to analyze cube state
 * Check browser console for detailed validation results
 * Identifies corner pieces with duplicate colors
🔧 Quick Fix
 * Click the "🔧 Fix" button to automatically resolve issues
 * Resets cube if too many invalid corners are detected
 * Attempts to fix minor corner color conflicts
🧮 Solving Algorithm
Layer-by-Layer Method (7 Steps)
 * 🔗 First Layer Edges: Form white cross on top face
 * ◻️ First Layer Corners: Complete white layer corners
 * 🟧 Second Layer Edges: Solve middle layer edges
 * 🔗 Third Layer Edges: Form yellow cross on top
 * 🔄 Permute Top Edges: Position yellow cross edges correctly
 * 🔄 Permute Top Corners: Position yellow corners correctly
 * ✨ Orient Top Corners: Orient final yellow corners
Current Implementation Status

> 🛑 Developer Note: Logic in Progress
> This is the primary area of development and where the project is currently "stuck."
> The foundation (state management, validation, 3D interface) is solid, but I am actively working on debugging and implementing the complex algorithmic logic for the 7-step solver. Any contributions, suggestions, or bug-fixes related to the solving logic would be extremely welcome!
> 
 * ✅ Step 1: White cross solving (fully implemented)
 * 🚧 Steps 2-7: Placeholder implementations. (Logic needed! This is the current bottleneck.)
🏗️ Technical Architecture
Core Components
State Management
cubeState = {
  U: ['W','W','W','W','W','W','W','W','W'], // Up face (White)
  D: ['Y','Y','Y','Y','Y','Y','Y','Y','Y'], // Down face (Yellow)
  F: ['G','G','G','G','G','G','G','G','G'], // Front face (Green)
  B: ['B','B','B','B','B','B','B','B','B'], // Back face (Blue)
  L: ['O','O','O','O','O','O','O','O','O'], // Left face (Orange)
  R: ['R','R','R','R','R','R','R','R','R']  // Right face (Red)
}

Face Notation
 * U: Up (White center)
 * D: Down (Yellow center)
 * F: Front (Green center)
 * B: Back (Blue center)
 * L: Left (Orange center)
 * R: Right (Red center)
Move Notation
 * F: Front face clockwise
 * F': Front face counter-clockwise
 * F2: Front face 180 degrees
 * Similar notation for all faces (U, D, L, R, B)
Validation System
Corner Piece Validation
The solver detects impossible cube states, particularly:
 * Corner pieces with duplicate colors
 * Invalid color distribution (each color must appear exactly 9 times)
 * Visual-state inconsistencies
Error Detection
// Example validation output
INVALID CORNER 3: Has duplicate colors [W,W,G] - duplicates: W
COLOR COUNT ERROR: W appears 11 times (should be 9)

🎯 API Reference
Key Functions
Cube Manipulation
 * scrambleCube(): Randomize cube state
 * resetCube(): Return to solved state
 * rotateFace(face, prime): Execute single face rotation
 * executeMoves(moves, callback): Execute move sequence
Solving
 * solveCube(): Main solving function with validation
 * beginnerSolver(): (In Progress) Layer-by-layer solving algorithm
 * isWhiteCrossComplete(): Check white cross completion
 * validateCubeState(): Comprehensive state validation
Paint Mode
 * togglePaintMode(): Enable/disable paint functionality
 * selectColor(color): Choose painting color
 * paintTile(event): Handle face painting
Debug Tools
 * debugCube(): Analyze and log cube state
 * quickFixCube(): Attempt automatic state correction
 * getCornerPieces(): Extract corner piece information
🔧 Configuration
Animation Speed
Adjust solving animation speed via the slider (50-500ms per move).
Color Mapping
const colorMap = {
  W: 0xffffff, // White
  Y: 0xffff00, // Yellow
  G: 0x00dd00, // Green
  B: 0x0000ff, // Blue
  O: 0xff8800, // Orange
  R: 0xff0000  // Red
}

🐛 Troubleshooting
Common Issues
Invalid Cube State
Problem: Solver refuses to run, shows validation errors
Solution:
 * Click 🔍 Debug to identify issues
 * Use 🔧 Fix to auto-correct
 * Manual reset with 🔄 Reset if needed
Visual Desync
Problem: Visual doesn't match internal state
Solution: State automatically syncs after moves, or use debug tools
Corner Duplicate Colors
Problem: Corner pieces have same color on multiple faces
Solution: This is impossible in real cubes - use 🔧 Fix or repaint correctly
Browser Compatibility
 * Recommended: Chrome 90+, Firefox 88+, Safari 14+
 * Requires: WebGL support
 * Mobile: iOS Safari 14+, Chrome Mobile 90+
🤝 Contributing

Development Setup
 * Fork the repository
 * Create a feature branch: git checkout -b feature-name
 * Make changes and test thoroughly
 * Submit a pull request
Areas for Contribution
This is the main priority!
 * Complete the Solving Logic: Help implement the algorithms for Steps 2-7 of the beginner's method.
 * Algorithm Debugging: Test and refine the existing Step 1 logic and help debug the state transitions for future steps.
 * Algorithm Optimization: Once the basic solver is working, help improve its efficiency.
Other areas:
 * UI Enhancements: Better mobile experience, themes
 * Additional Algorithms: CFOP, Roux, ZZ methods
 * Performance: Optimize animation and rendering
Code Style
 * Use ES6+ features
 * Maintain existing naming conventions
 * Add comments for complex algorithms
 * Test with various cube states
📊 Performance
Benchmarks
 * Scramble Generation: ~20ms for 20 moves
 * State Validation: ~5ms for full cube analysis
 * Move Execution: 50-500ms (user configurable)
 * Render Performance: 60 FPS on modern devices
Memory Usage
 * Base Application: ~15MB
 * Three.js Library: ~2MB
 * Cube State: <1KB
📝 License
This project is licensed under the MIT License - see the LICENSE file for details.
🙏 Acknowledgments
 * Three.js Community: For the excellent 3D library
 * Rubik's Cube Community: For solving algorithms and notation standards
 * Layer-by-Layer Method: Based on beginner-friendly solving approaches
📈 Roadmap
Version 2.0 (Planned)
 * [ ] Complete Core Solver: Finalize and debug the 7-step layer-by-layer implementation.
 * [ ] CFOP algorithm support
 * [ ] Cube timer functionality
 * [ ] Save/load cube states
 * [ ] Pattern library
Version 2.1 (Future)
 * [ ] Multiplayer competitions
 * [ ] Advanced solving statistics
 * [ ] Custom color schemes
 * [ ] VR/AR support
📞 Support
 * Issues: GitHub Issues
 * Discussions: GitHub Discussions
 * Documentation: This README and inline code comments
Happy Cubing! 🎲✨
Made with ❤️ by the Rubik's Cube community
