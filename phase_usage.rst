
***************************
Phase Usages
***************************

List of phase used in UVM. For each phase has used for unique operations


build_phase
============================
* Instantiate sub-components.
* Instantiate register model.
* Get configuration values for the component being built.
* Set configuration values for sub-components

connect_phase
============================
* Connect TLM ports and exports.
* Connect TLM initiator sockets and target sockets.
* Connect register model to adapter components.
* Setup explicit phase domains

end_of_elaboration_phase
============================
* Display environment topology.
* Open files.
* Define additional configuration settings for components.

start_of_simulation_phase
============================
* Display environment topology
* Set debugger breakpoint
* Set initial run-time configuration values

run_phase
============================
* Components implement behavior that is exhibited for the entire run-time, across the various run-time phases.
* Backward compatibility with OVM

pre_reset_phase
----------------------------
* Wait for power good.
* Components connected to virtual interfaces should initialize their output to X’s or Z’s.
* Initialize the clock signals to a valid value Assign reset signals to X (power-on reset).
* Wait for reset signal to be asserted if not driven by the verification environment.

reset_phase
----------------------------
* Assert reset signals.
* Components connected to virtual interfaces should drive their output to their specified reset or idle value.
* Components and environments should initialize their state variables.
* Clock generators start generating active edges.
* De-assert the reset signal(s) just before exit.
* Wait for the reset signal(s) to be de-asserted.


post_reset_phase
----------------------------
* Components should start behavior appropriate for reset being inactive. 
For example, 
    components may start to transmit idle transactions or interface training and rate negotiation. 
    This behavior typically continues beyond the end of this phase.

pre_configure_phase
----------------------------
* Procedurally modify the DUT configuration information as described in the environment (and that will be eventually uploaded into the DUT).
* Wait for components required for DUT configuration to complete training and rate negotiation.


configure_phase
----------------------------
* Components required for DUT configuration execute transactions normally.
* Set signals and program the DUT and memories (e.g. read/write operations and sequences) to match the desired configuration for the test and environment.


post_configure_phase
----------------------------
* Wait for configuration information to fully propagate and take effect.
* Wait for components to complete training and rate negotiation.
* Enable the DUT.
* Sample DUT configuration coverage

pre_main_phase
----------------------------
* Wait for components to complete training and rate negotiation

main_phase
----------------------------
* Components execute transactions normally.
* Data stimulus sequences are started.
* Wait for a time-out or certain amount of time, or completion of stimulus sequences

post_main_phase
----------------------------
* Included for symmetry.

pre_shutdown_phase
----------------------------
* Included for symmetry.

shutdown_phase
----------------------------
* Wait for all data to be drained out of the DUT.
* Extract data still buffered in the DUT, usually through read/write operations or sequences.

post_shutdown_phase
----------------------------
* Perform final checks that require run-time access to the DUT (e.g. read accounting
  registers or dump the content of memories).




extract_phase
============================
* Extract any remaining data and final state information from scoreboard and testbench components
* Probe the DUT (via zero-time hierarchical references and/or backdoor accesses) for final state information.
* Compute statistics and summaries.
* Display final state information
* Close files.

check_phase
============================
* Check that no unaccounted-for data remain.

report_phase
============================
* Report test results.
* Write results to file

final_phase
============================
* Close files.
* Terminate co-simulation engines




