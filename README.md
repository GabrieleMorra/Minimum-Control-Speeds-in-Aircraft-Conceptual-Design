# Minimum Control Speeds in Aircraft Conceptual Design

[![License: BSD 3-Clause](https://img.shields.io/badge/License-BSD%203--Clause-blue.svg)](https://opensource.org/licenses/BSD-3-Clause)
[![DOI](https://img.shields.io/badge/DOI-10.1016%2Fj.ast.2025.110856-blue)](https://doi.org/10.1016/j.ast.2025.110856)
[![Platform](https://img.shields.io/badge/Platform-Windows%20|%20Linux%20|%20macOS-lightgrey)](https://dotnet.microsoft.com/)
[![Language](https://img.shields.io/badge/Language-C%23-239120)](https://docs.microsoft.com/en-us/dotnet/csharp/)
A scientific software tool for calculating aircraft minimum control speeds (Vmca and Vmcg) using lateral-directional trim analysis, implementing the methodology described in the research paper "Lateral-Directional Trim For Air And Ground Minimum Control Speeds Evaluation In Conceptual Design".

## Overview

This software calculates two critical aircraft performance parameters:
- **Vmca (Air Minimum Control Speed)**: Minimum speed for maintaining directional control in flight after an engine failure
- **Vmcg (Ground Minimum Control Speed)**: Minimum speed for maintaining directional control during takeoff ground roll after an engine failure

The calculations are based on rigorous aerodynamic analysis using Roskam procedures, nonlinear trim solving, and time-domain simulation for ground maneuvers.

## Scientific Background

The software implements the methodology published in:
> Morra, G. (2025). Lateral-Directional Trim For Air And Ground Minimum Control Speeds Evaluation In Conceptual Design. *Aerospace Science and Technology*. https://doi.org/10.1016/j.ast.2025.110856

### Key Features

- **Advanced Aerodynamic Modeling**: Uses Roskam procedures for calculating aerodynamic derivatives
- **Nonlinear Trim Analysis**: Solves trim equations using numerical optimization
- **Ground Simulation**: Time-domain analysis of ground maneuvers with tire-runway interaction
- **ISA Atmosphere Modeling**: Accurate atmospheric property calculations
- **Engine Modeling**: Supports both turboprop and turbofan thrust deck interpolation
- **Regulatory Compliance**: Calculations align with FAR/EASA certification requirements

## System Requirements

- Windows operating system
- Microsoft Excel (for input interface)
- .NET Framework runtime

## Installation

1. Download the latest release from the [release](release) folder
2. Ensure all DLL files are in the same directory as `vmc.exe`:
   - `MathNet.Numerics.dll`
   - `HSG.Numerics.dll`
   - `OptimizationToolbox.dll`
   - `StarMath.dll`
   - `C.Numerics.dll`
   - `FSharp.Core.dll`

## Usage

### Quick Start

1. Open `vmc analysis.xlsm` in Microsoft Excel
2. Navigate to the **Input** sheet
3. Enter your aircraft parameters and flight conditions
4. Save the Excel file
5. Run `vmc.exe` by double-clicking or within the Excel file using the button
6. Results will be written to the **Output** sheet in Excel

### Algorithm Configuration

The software supports various analysis modes:
- Simplified VMCG analysis: solves the simple equilibrium between OEI yawing moment and rudder control yaw
- VMCA analysis with variable bank angle: it is possible to set the array of bank angles
- VMCA analysis with variable mass: it is possible to set the array of masses
- VMCA analysis for different atmospheric conditions: it is possible to set the arrays of altitude, pressure and ISA temperature displacement
- Detailed VMCG analysis: ground simulation to find the highest speed that satisfies the 30ft lateral displacement requirement  

## Examples

The software has been validated against real aircraft data:

### Lockheed C-130J Hercules
- Military transport aircraft
- Turboprop configuration
- STOL capabilities

### ATR 72-500
- Regional airliner
- Twin turboprop
- Commercial certification

Example input files for both aircraft are provided in the Excel file "vmc analysis.xlsm".

## Output

The software calculates:
- **Vmca**: Air minimum control speed (knots)
- **Vmcg**: Ground minimum control speed (knots)
- **Trim conditions**: Control surface deflections, sideslip angles
- **Aerodynamic derivatives**: Stability and control derivatives
- **Performance margins**: Safety factors and certification compliance

## Technical Implementation

### Architecture
- **Language**: C# .NET Framework
- **Excel Integration**: COM interop for seamless data exchange
- **Numerical Libraries**: MathNet.Numerics, HSG.Numerics
- **Optimization**: Nonlinear solvers for trim calculations

### Calculation Methodology
1. **Aerodynamic Analysis**: Calculate stability and control derivatives using Roskam methods
2. **Trim Solution**: Solve nonlinear equilibrium equations for lateral-directional trim
3. **Speed Determination**: Find minimum speeds satisfying control authority limits
4. **Ground Simulation**: Time-domain analysis for ground roll scenarios

## Validation

The software has been extensively validated against:
- Published aircraft data
- Wind tunnel test results  
- Flight test measurements
- Certification documentation

Validation results show excellent agreement with experimental data, with typical errors below 5% for most aircraft configurations.

## License

This software is released under the 3-Clause BSD License. See [LICENSE](LICENSE) file for details.

## Citation

If you use this software in your research, please cite:

```bibtex
@article{morra2025lateral,
  title={Lateral-Directional Trim For Air And Ground Minimum Control Speeds Evaluation In Conceptual Design},
  author={Morra, Gabriele and Mirabella, Claudio and Nicolosi, Fabrizio and Della Vecchia, Pierluigi},
  journal={Aerospace Science and Technology},
  pages={110856},
  year={2025},
  publisher={Elsevier},
  doi={10.1016/j.ast.2025.110856}
}
```

## Authors

**Gabriele Morra**, **Claudio Mirabella**, **Fabrizio Nicolosi**, **Pierluigi Della Vecchia**  
University of Naples Federico II, Department of Industrial Engineering

## Support

For questions, bug reports, or feature requests, please open an issue on GitHub or contact the corresponding author.

---

*This software is provided for research and educational purposes. Users are responsible for verifying results for their specific applications.*