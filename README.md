# Metal CNC Feeds & Speeds Calculator

A web-based feeds and speeds calculator designed for the **Genmitsu PROVer MAX 3030 CNC** with **Carbide Compact Router (CCR)** at the Mason Innovation Exchange (MIX) Fabrication Lab. This educational tool helps students safely machine metal materials with conservative, hobby-CNC-appropriate parameters.

[![Status](https://img.shields.io/badge/Status-Active-success)](https://github.com/YOUR_USERNAME/metal-cnc-calculator)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Made with Love](https://img.shields.io/badge/Made%20with-❤️-red.svg)](https://github.com/YOUR_USERNAME/metal-cnc-calculator)

---

## 📸 Screenshots

<!-- Main Interface -->
<img width="842" height="1012" alt="image" src="https://github.com/user-attachments/assets/1b260398-b3da-4712-b5e5-ca8aa22fafe7" />


*Main calculator interface with material and operation selection*

<!-- Results Display -->
<img width="850" height="963" alt="image" src="https://github.com/user-attachments/assets/7428cf88-438f-4a25-a4d0-9f91670b7e7f" />


*Example calculation results with safety warnings*

---

## 🎯 Purpose

This calculator was developed specifically for **student safety** and **educational use** on hobby CNC machines. It provides conservative cutting parameters based on material type, operation, tool geometry, and flute count to prevent:

- Tool breakage
- Part damage  
- Machine chatter
- Chip welding (especially in aluminum)

---

## ✨ Features

### Intelligent Flute-Based Parameters

- **Adaptive ADOC & RDOC**: Automatically adjusts Axial Depth of Cut (DOC) and Radial Depth of Cut (stepover) based on the number of flutes
- **Material-Specific Tables**: Optimized parameters for each material (Aluminum 6061, Polycarbonate, Brass, Copper, Mild Steel)
- **Safety Warnings**: Alerts for incompatible tool/material combinations (e.g., 4-flute in copper, 3-4 flute in mild steel)

### Operation Types

1. **Contour Profiling** - Outside/inside profiles with 50% WOC (side milling)
2. **Slotting** - Full width engagement (100% WOC) with reduced parameters
3. **Pocketing** - Adaptive clearing with flute-optimized stepover (20% default for 2-flute)
4. **3D Roughing** - Variable depth clearing for 3D models
5. **3D Finishing** - Fine detail passes for smooth surfaces

### Bit Type Support

- **Flat End Mill** - Standard all-purpose (1.0× multipliers)
- **Ball Nose** - 3D contours and finishing (0.85× chipload, 0.75× depth)
- **V-Bit/Engraving** - Chamfering and detail work (0.7× chipload, 0.5× depth)
- **Roughing End Mill** - Aggressive material removal (1.2× chipload, 1.3× depth)

### Safety Features

**Aluminum-Specific Rules:**
- DOC cap: 15-25% of tool diameter
- Feed rate limit: 55 IPM maximum
- Chipload cap: 0.0016" per tooth maximum

**Additional Safety:**
- Long tool warnings (stickout > 3× diameter)
- Real-time chipload validation with color-coded feedback
- Material-specific cooling requirements
- Incompatible tool/material alerts

### Calculated Outputs

All results shown in both **inches and millimeters**:

- Feed Rate (in/min, mm/min)
- Plunge Rate (in/min, mm/min)
- Depth per Pass (inches, mm) + number of passes needed
- Stepover/WOC (inches, mm, percentage)
- Ramp Distance (inches, mm, angle)
- Material Removal Rate (in³/min, mm³/min)

---

## 🛠️ Supported Materials

| Material | Best Tool | ADOC Range (2-flute) | RDOC Range (2-flute) | Notes |
|----------|-----------|----------------------|----------------------|-------|
| **Aluminum 6061** | 1-flute O-flute | 15-25% | 15-25% | Prone to chip welding; use cooling |
| **Polycarbonate** | 1-2 flutes | 30-60% | 30-50% | Can melt from heat; use air blast |
| **Brass** | 1-2 flutes | 15-30% | 15-25% | Machines well; support thin features |
| **Copper** | 1-flute only | 8-15% | 8-15% | Soft and gummy; 4-flute not recommended |
| **Mild Steel** | 1-2 flutes | 5-10% | 5-10% | Router-limit material; 3-4 flutes not recommended |

---

## 💻 Technology Stack

- **Pure HTML/CSS/JavaScript** - No external dependencies
- **Single-file application** - Easy to deploy and share
- **Responsive design** - Works on desktop, tablet, and mobile
- **Dark theme** - Reduced eye strain in workshop environments

---

## 🚀 Usage

### Online Access

Try it live: [Metal CNC Calculator](https://YOUR_USERNAME.github.io/metal-cnc-calculator/metal-cnc-calculator.html)

### Local Installation

```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/metal-cnc-calculator.git

# Navigate to directory
cd metal-cnc-calculator

# Open in browser
open metal-cnc-calculator.html  # macOS
start metal-cnc-calculator.html  # Windows
xdg-open metal-cnc-calculator.html  # Linux
```

### Basic Workflow

1. **Select Material** (e.g., Aluminum 6061)
2. **Select Operation Type** (e.g., Pocketing)
3. **Select Bit Type** (e.g., Flat End Mill)
4. **Select Tool Diameter** (e.g., 1/8")
5. **Select Number of Flutes** (e.g., 2 Flutes)
6. **Enter Target Chipload** (e.g., 0.001" - safe range shown below input)
7. **Enter Total Cut Depth** (e.g., 1.5 mm)
8. **Enter Spindle RPM** (default: 18,000)
9. Click **"Calculate Feeds & Speeds"**

---

## 📊 Example Calculation

### Input Configuration

```
Material:           Aluminum 6061
Operation:          Pocketing (Adaptive Clearing)
Bit Type:           Flat End Mill
Tool Diameter:      1/8" (0.125")
Number of Flutes:   2
Spindle RPM:        18,000
Target Chipload:    0.001"
Total Cut Depth:    5.0 mm (0.197")
Plunge Factor:      25%
```

### Calculated Results

```
Feed Rate:          36.0 in/min (914 mm/min) ✓ Safe
Plunge Rate:        9.0 in/min (229 mm/min)
Depth per Pass:     0.025" (0.635 mm) → 8 passes needed
Stepover (RDOC):    0.025" (0.635 mm) at 20% (flute-optimized)
Ramp Distance:      0.477" (12.1 mm) at 3° angle
Material Removal:   0.023 in³/min (370 mm³/min)
```

### Safety Notes

```
✓ Safe Feed Rate: 36.0 in/min is in the safe range (45-55 in/min) for aluminum
⚠️ Long Tool Warning: If tool stickout is long (>3x diameter), 
   reduce stepover to 10% and reduce depth per pass by 50%
💡 Soft and gummy - chips can weld to tool. Use sharp tools, 
   1-2 flute endmills. For chip welding: reduce RPM to 16-18k, 
   increase feed rate.
```

---

## 🎓 Educational Use

This calculator is designed as a **learning tool** for students at the MIX Fabrication Lab. Key pedagogical features:

- **Manual Input Required**: No pre-filled defaults force students to understand each parameter
- **Safe Ranges Shown**: Recommendations appear dynamically to guide decision-making
- **Conservative Parameters**: All defaults prioritize safety over speed
- **Real-time Feedback**: Color-coded validation helps students learn safe ranges
- **Clear Warnings**: Operation-specific tips and material notes provide context

---

## ⚙️ Technical Details

### Spindle Speed Mapping

Carbide Compact Router (CCR) dial settings:

| Dial Setting | RPM |
|--------------|-----|
| 1 | 10,000 |
| 2 | 14,000 |
| 3 | 18,000 |
| 4 | 22,000 |
| 5 | 26,000 |
| 6 | 30,000 |

### Formula Reference

```javascript
// Feed Rate Calculation
feedRate = rpm × flutes × chipload × bitTypeMultiplier

// Plunge Rate Calculation  
plungeRate = feedRate × plungeFactor  // Default: 25%

// Depth Per Pass Calculation
depthPerPass = toolDiameter × materialFactor × operationFactor × bitTypeFactor

// Stepover Calculation
stepover = toolDiameter × (stepoverPercent / 100)

// Ramp Distance Calculation
rampDistance = depth / tan(rampAngle)

// Material Removal Rate
MRR = feedRate × depth × stepover
```

### Flute-Based Parameter Tables

**Aluminum 6061 Pocketing:**

```javascript
depthFactorByFlutes: {
    1: 0.175,  // 17.5% of tool diameter
    2: 0.20,   // 20% of tool diameter
    3: 0.15,   // 15% of tool diameter
    4: 0.10    // 10% of tool diameter
}

stepoverPercentByFlutes: {
    1: 25,     // 25% of tool diameter
    2: 20,     // 20% of tool diameter
    3: 15,     // 15% of tool diameter
    4: 10      // 10% of tool diameter
}
```

---

## 🔧 Software Integration

### Recommended Workflow

```
1. Metal CNC Calculator
   ↓ (Calculate safe parameters)
   
2. VCarve Pro
   ↓ (Input mm values, generate toolpaths)
   
3. Candle Controller
   ↓ (Load G-code)
   
4. Genmitsu PROVer MAX 3030
   ↓ (Execute cut)
```

**Note:** VCarve Pro accepts millimeters even when using imperial bits. The calculator provides mm conversions for convenience.

---

## 📁 Project Structure

```
metal-cnc-calculator/
├── README.md                      # Project documentation
├── LICENSE                        # MIT License
├── metal-cnc-calculator.html      # Main application (single file)
└── screenshots/                   # Interface screenshots
    ├── main-interface.png
    ├── results-display.png
    └── mobile-view.png
```

---

## 🤝 Contributing

Contributions, suggestions, and improvements are welcome!

### Reporting Issues

If you encounter bugs or have feature requests, please [open an issue](https://github.com/YOUR_USERNAME/metal-cnc-calculator/issues) with:

- Material and operation being used
- Expected vs. actual behavior
- Screenshots if applicable

### Development

The codebase is intentionally kept as a single HTML file for maximum portability.

**To contribute:**

```bash
# Fork the repository
# Clone your fork
git clone https://github.com/YOUR_USERNAME/metal-cnc-calculator.git

# Create a feature branch
git checkout -b feature/your-feature-name

# Make changes and commit
git add metal-cnc-calculator.html
git commit -m "Add feature: your feature description"

# Push to your fork
git push origin feature/your-feature-name

# Create Pull Request on GitHub
```

### Future Enhancements

- [ ] Additional materials (acrylic, bronze, stainless steel)
- [ ] Imperial/metric unit toggle for all inputs
- [ ] Save/load parameter presets
- [ ] Export results to PDF
- [ ] Mobile app version
- [ ] Multiple language support
- [ ] Integration with popular CAM software

---

## 📝 License

MIT License - See [LICENSE](LICENSE) file for details

```
MIT License

Copyright (c) 2025 Tan Chau

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction...
```

---

## 👨‍💻 Author

**Tan Chau**  
Makerspace Associate, Mason Innovation Exchange (MIX) Fabrication Lab  
George Mason University

- **Email:** minten2806@gmail.com
- **LinkedIn:** [Minh Tan Chau](https://www.linkedin.com/in/minh-tan-chau/)
- **Portfolio:** [Tan Chau - Mechanical Engineer & Fabrication Specialist](https://tankgvn.github.io/)
- **YouTube:** [@TenGineerin9](https://youtube.com/@TenGineerin9)

---

## 🙏 Acknowledgments

- **George Mason University** - MIX Fabrication Lab
- **Office of International Programs and Services (OIPS)** - Support and guidance
- **Students and Faculty** - Feedback during development and testing
- **CNC Machining Community** - Best practices and safety guidelines

---

## ⚠️ Disclaimer

This calculator provides **recommendations only**. 

**Always:**
- Start with conservative parameters and test on scrap material
- Wear appropriate safety equipment (safety glasses, hearing protection)
- Follow lab safety protocols and machine operating procedures
- Inspect tools for damage before use
- Monitor first passes closely for chatter, excessive noise, or poor finish
- Adjust parameters based on actual cutting performance
- Consult with lab staff if uncertain

**The authors and George Mason University are not responsible for:**
- Tool breakage or machine damage
- Part damage or material waste
- Personal injury resulting from use of these parameters
- Any consequences of improper machine operation

**When in doubt, ask for help!**

---

## 📚 Additional Resources

### Learning CNC Machining
- [CNC Cookbook - Feeds & Speeds Guide](https://www.cnccookbook.com/feeds-speeds-basic-cnc-tutorial/)
- [MIT Machine Shop - CNC Training](https://studentshops.mit.edu/machine-shop/)
- [NYC CNC - YouTube Channel](https://www.youtube.com/@nycCNC)
- [Haas Automation - CNC Training](https://www.haascnc.com/education.html)

### VCarve Pro Resources
- [VCarve Pro Official Documentation](https://help.vectric.com/docs/V11.5/VCarvePro/ENU/Help/VCarve%20Pro.htm)
- [Vectric YouTube Channel](https://www.youtube.com/@VectricLtd)

### Genmitsu Resources
- [Genmitsu PROVer MAX Product Page](https://www.sainsmart.com/products/genmitsu-prover-max-3030)
- [SainSmart Knowledge Base](https://www.sainsmart.com/pages/knowledge-base)

---

**Made with ❤️ for MIX Workshop by Tan Chau**

`Genmitsu PROVer MAX 3030 | Carbide Compact Router (CCR) | VCarve Pro | Candle`
