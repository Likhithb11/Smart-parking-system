# Smart-parking-system
Verilog code for smart parking system 
// Smart Parking System

module SmartParkingSystem(
    input clk, // clock input
    input reset, // asynchronous reset input
    input sensor1, // sensor 1 input
    input sensor2, // sensor 2 input
    output reg led // LED output
);

reg state; // state variable to track parking lot occupancy

always @(posedge clk, negedge reset) begin
    if (reset == 0) begin
        state <= 0; // reset to initial state
        led <= 1; // turn off LED
    end else begin
        if (sensor1 == 1 && sensor2 == 1 && state == 0) begin
            state <= 1; // car parked
            led <= 0; // turn on LED
        end else if (sensor1 == 0 && sensor2 == 0 && state == 1) begin
            state <= 0; // car left
            led <= 1; // turn off LED
        end
    end
end

endmodule
