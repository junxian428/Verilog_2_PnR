# Verilog_2_PnR

To convert a Verilog design to Place and Route (P&R) files, you'll typically go through a series of steps that include synthesis, place and route, and various verification checks. Below is a structured guide outlining the necessary steps and tools involved in this process:

### Steps to Convert Verilog to P&R Files

1. **Design Entry**:
   
   - Write your design in Verilog (or VHDL) and save it in a `.v` file.

3. **Synthesis**:
   - Use a synthesis tool to convert the Verilog code into a gate-level netlist. This netlist contains the logical representation of your design using standard cells.
     
   - Common synthesis tools include:
     
     - **Synopsys Design Compiler**
       
     - **Cadence Genus**
       
     - **Xilinx Vivado** (for FPGA designs)

   **Command Example (using Synopsys Design Compiler)**:

   ```bash
   
   dc_shell -f synthesize.tcl
   
   ```

5. **Technology Library**:
   
7. - Ensure you have the appropriate technology library (.lib files) that defines the characteristics of the standard cells for your target process technology.
     

8. **Generate a Standard Cell Netlist**:

9. 
   - After synthesis, you will get a netlist (often in `.v` or `.db` format) that is used for the next steps.

10. **Floorplanning**:
   - Use a Place and Route tool to perform floorplanning. Define the chip's layout, including the placement of functional blocks and the overall dimensions.

11. **Place and Route (P&R)**:
    
   - Load the synthesized netlist into a P&R tool. The tool will perform placement of standard cells and then route the interconnections based on the netlist.
     
   - Common P&R tools include:
     
     - **Cadence Innovus**
       
     - **Synopsys ICC (Innovative Chip Compiler)**
       
     - **Mentor Graphics Olympus-SoC**

   **Command Example (using Cadence Innovus)**:
  
   ```bash

   innovus -init floorplan.tcl

   ```

11. **DRC and LVS Checks**:
    
   - After routing, perform Design Rule Checks (DRC) to ensure the layout complies with manufacturing rules.
     
   - Conduct Layout Versus Schematic (LVS) checks to verify that the physical layout matches the netlist.
   
   **Command Example for DRC (using Cadence)**:
  
   ```bash

   run_drc

   ```

11. **Extract Parasitics**:
    
   - Extract parasitics from the layout to get an accurate representation of the circuit’s electrical behavior.

11. **Timing Analysis**:
    
   - Perform Static Timing Analysis (STA) on the extracted netlist to verify that the design meets the required timing constraints.

11. **GDSII Generation**:
    
   - Finally, generate the GDSII file, which contains the physical layout data for fabrication.
   
   **Command Example (using Cadence)**:
   
   ```bash

   gdsii_write -output design.gds

   ```

### Summary of Output Files

- **Netlist File**: The synthesized netlist, often in `.v` or `.db` format.
  
- **P&R Layout File**: The physical layout of the design, typically in GDSII format (`.gds`).
  
- **DRC Report**: A report detailing any design rule violations.
  
- **LVS Report**: A report verifying that the layout matches the netlist.
  
- **Timing Reports**: Reports detailing the timing analysis results.

### Note

- The exact commands and steps may vary based on the specific tools you are using. Always refer to the tool documentation for the correct usage and syntax.
  
- It’s essential to have the necessary licenses for the EDA tools and to follow the guidelines provided by the foundry for the specific technology being used.

By following these steps, you can successfully convert your Verilog design into P&R files ready for fabrication.
