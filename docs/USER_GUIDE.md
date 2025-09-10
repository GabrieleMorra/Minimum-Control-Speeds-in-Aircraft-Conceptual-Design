# User Guide: Minimum Control Speeds Calculator

This guide provides detailed instructions for using the minimum control speeds calculation software.

## Workflow Overview

The software follows a three-step process, as described in the research paper:
1. **Input**: Enter aircraft parameters in Excel
2. **Calculation**: Run the executable to perform analysis
3. **Output**: Review results in Excel

## Step-by-Step Instructions

### 1. Preparing Input Data

Open `vmc analysis.xlsm` in Microsoft Excel and navigate to the **Input** sheet.

#### Aircraft Configuration

**Fuselage Parameters**
- `Fuselage Reference Diameter` (m): average diameter of the fuselage central trunk 
- `Fuselage Diameter At Vertical Tail Quarter Chord ` (m): fuselage diameter at the longitudinal position of the vertical tail quarter chord
- `Fuselage Length` (m): total length of the fuselage from nose to tail
- `Fuselage Section Area S0` (m²): cross-sectional area of the fuselage at the reference station (see Roskam Part VI, Pag. 385, Fig. 10.10)
- `Fuselage volume` (m³): total internal volume of the fuselage

**Horizontal Tail**
- `Horizontal Surface` (m²): horizontal tail planform area
- `Horizontal Span` (m): horizontal tail span from tip to tip
- `Horizontal Sweep Half Chord` (deg): sweep angle of the horizontal tail half-chord line
- `Horizontal Z`(m): vertical position of horizontal tail relative to fuselage centerline
- `Horizontal η` (): ratio between horizontal tail dynamic pressure and wing dynamic pressure 

**Vertical Tail**
- `Vertical Rudder Chord Fraction`: ratio of rudder chord to vertical tail chord
- `Vertical Span` (m): height of the vertical tail from root to tip
- `Vertical Sweep Quarter Chord` (deg): sweep angle of the vertical tail quarter-chord line
- `Vertical Chord Root` (m): chord length at the root of the vertical tail
- `Vertical Chord Tip` (m): chord length at the tip of the vertical tail
- `Vertical Z` (m): vertical position of vertical tail root above fuselage centerline
- `Vertical L` (m): longitudinal distance from aircraft CG to vertical tail aerodynamic center
- `Vertical Rudder Maximum Deflection` (deg): maximum rudder deflection angle
- `Vertical Rudder / Vertical Span` (%): ratio of rudder span to total vertical tail span
- `Vertical Thickness/Chord Ratio at Rudder Station` (%): airfoil thickness-to-chord ratio at rudder station

**Wing Geometry**
- `Wing Surface` (m²): wing planform area
- `Wing Span` (m): wing span from tip to tip
- `Wing Dihedral` (deg): wing dihedral angle
- `Wing Height` (m): vertical position of wing relative to fuselage centerline (negative if wing is upper)
- `Wing Average Sweep (of the equivalent wing)` (deg): average sweep angle of the wing
- `Wing Aileron Maximum Deflection` (deg): maximum aileron deflection angle
- `Wing Taper Ratio` (): ratio of wing tip chord to root chord
- `Wing Tip X Position` (m): longitudinal position of wing tip relative to fuselage nose
- `Wing Geometric Twist` (deg): geometric twist angle from root to tip
- `Wing Thickness/Chord Ratio at Aileron Station` (%): airfoil thickness-to-chord ratio at aileron station
- `Wing Aileron Chord Fraction` (): ratio of aileron chord to wing chord
- `Wing Airfoil Lift Curve Slope at Aileron Station` (rad⁻¹): lift curve slope of wing airfoil at aileron station
- `Wing Aileron Inner Position / Wing Span` (%): inner boundary of aileron relative to wing semi-span
- `Wing Aileron Outer Position / Wing Span` (%): outer boundary of aileron relative to wing semi-span

**Aerodynamic behaviour**
- `CL max TO` (): maximum lift coefficient in takeoff configuration
- `CL ground` (): lift coefficient during ground operations

**Engine Configuration**
- `Engine Type: TurboProp (TP), TurboFan (TF)` (): engine type designation
- `Number Of Engines` (): total number of engines on aircraft
- `Nacelle Reference Diameter` (m): reference diameter of engine nacelle
- `Max Static Thrust` (N): maximum static thrust per engine at sea level
- `Y thust axis` (m): lateral distance of thrust axis from aircraft centerline

**Setup for VMCG analysis**
- `Rz bar` (): non-dimentional z radius of giration (see Roskam Part V, Appendix B)
- `Rudder Angular Velocity` (deg·s⁻¹): rate of rudder deflection during maneuver
- `Operating Empty Mass` (kg): aircraft mass without payload and fuel
- `CD0 Takeoff` (): zero-lift drag coefficient in takeoff configuration
- `oswald` (): Oswald efficiency factor for induced drag calculation
- `xm` (m): longitudinal position of main landing gear
- `xn` (m): longitudinal position of nose landing gear
- `ym` (m): lateral distance of main landing gear from centerline

#### Flight Conditions

- `Flight Height` (ft): altitude for analysis
- `Flight ISA Deviation` (°C): temperature deviation from International Standard Atmosphere
- `Mach` (): Mach number for analysis
- `Mass` (kg): aircraft mass for analysis
- `Max Side Displacement (Vmcg)` (ft): maximum allowable lateral displacement during ground maneuver

#### Algorithm Setup

**Analysis Flags**
- `Data Input Column`: column number in Excel for data input
- `Folder path`: file path for output results
- `Run Simplified Vmcg analysis`: flag to enable simplified VMCG calculation
- `Run Vmca analysis φ fixed`: flag to run VMCA analysis with fixed bank angle
- `Start φ vector [deg]`: initial bank angle for parametric study
- `Step φ vector [deg]`: bank angle increment for parametric study
- `End φ vector [deg]`: final bank angle for parametric study
- `Run Vmca analysis for several masses`: flag to enable mass parametric study
- `Start mass vector [kg]`: initial mass for parametric study
- `Step mass vector [kg]`: mass increment for parametric study
- `End mass vector [kg]`: final mass for parametric study
- `Run Vmca analysis for different atm conditions`: flag to enable atmospheric conditions study
- `Start height vector [ft]`: initial altitude for parametric study
- `Step height vector [ft]`: altitude increment for parametric study
- `End height vector [ft]`: final altitude for parametric study
- `Start ΔISA vector [°C]`: initial ISA deviation for parametric study
- `Step ΔISA vector [°C]`: ISA deviation increment for parametric study
- `End ΔISA vector [°C]`: final ISA deviation for parametric study
- `Run detailed Vmcg analysis for different atms`: flag to enable detailed VMCG analysis with atmospheric variations


### 2. Running the Calculation

1. **Save the Excel file** after entering all parameters
2. **Run the executable**:
   - Click `Run vmc.exe` in the Excel file, or
   - Double-click the file: `vmc.exe`

The software will:
- Read input parameters from the Excel file
- Perform aerodynamic calculations
- Solve trim equations
- Calculate minimum control speeds
- Write results back to Excel in the **Output** sheet

### 3. Interpreting Results

Open the Excel file and navigate to the **Output** sheet to view results.

#### Primary Results

**VMCA (Air Minimum Control Speed)**
- `Vmca CAS` (knots): Calculated air minimum control speed
- `Standardized Vmca Flight Manual CAS` (knots): Calculated standardized air minimum control speed
- `β` (deg): Sideslip angle at VMCA
- `δr` (deg): Rudder deflection at VMCA
- `δa` (deg): Aileron deflection at VMCA
- `φ` (deg): Bank angle at VMCA

**VMCG (Ground Minimum Control Speed)**
- `Vmcg` (knots): Calculated ground minimum control speed
- Associated ground maneuver parameters

#### Aerodynamic Derivatives

The output includes calculated stability and control derivatives:
- `CY β`: Side force due to sideslip
- `CL β`: Rolling moment due to sideslip
- `CN β`: Yawing moment due to sideslip
- `CY δr`: Side force due to rudder
- `CL δr`: Rolling moment due to rudder
- `CN δr`: Yawing moment due to rudder
- `CY δa`: Side force due to aileron
- `CL δa`: Rolling moment due to aileron
- `CN δa`: Yawing moment due to aileron

#### Atmospheric Properties

- `Height` (ft): Pressure altitude
- `Air density` (kg/m³): Air density
- `ΔISA` (°C): ISA temperature deviation 
- `OAT` (°C): Outside air temperature 

### 4. Validation and Verification

#### Check Input Data
- Verify all geometric parameters are consistent
- Ensure mass and center of gravity are realistic
- Check that control surface dimensions are within wing bounds

#### Validate Results
- Compare with similar aircraft if available
- Check that control surface deflections are within realistic limits
- Verify that calculated speeds are reasonable for the aircraft type

#### Troubleshooting Common Issues

**Unrealistic Results**
- Review input parameters for errors
- Check units (metric system used throughout)
- Verify engine position and thrust values

## Example Workflows

### Quick Analysis
1. Use default parameters as starting point
2. Modify key parameters (mass, CG, altitude)
3. Run calculation
4. Review primary results

## Best Practices

### Data Management
- Keep backup copies of input files
- Document parameter sources and assumptions
- Maintain version control for analysis iterations

### Result Interpretation
- Cross-check results with handbook methods
- Consider uncertainty and sensitivity
- Validate against flight test or published data when available

## Technical Support

For technical questions or issues:
1. Check this user guide first
2. Review the README.md file
3. Open an issue on the GitHub repository
4. Contact the author directly

Remember to include:
- Input parameter values
- Error messages if any
- System configuration details
- Expected vs. actual results