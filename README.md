# SR_FLIP_FLOP

AIM:

To implement SR flipflop using verilog and validating their functionality using their functional tables

SOFTWARE REQUIRED:

Quartus prime

THEORY

SR Flip-Flop SR flip-flop operates with only positive clock transitions or negative clock transitions. Whereas, SR latch operates with enable signal. The circuit diagram of SR flip-flop is shown in the following figure.

<img width="725" height="415" alt="Screenshot 2025-12-13 190001" src="https://github.com/user-attachments/assets/ddd3d816-02d4-4076-98af-272538840a3b" />

This circuit has two inputs S & R and two outputs Qtt & Qtt’. The operation of SR flipflop is similar to SR Latch. But, this flip-flop affects the outputs only when positive transition of the clock signal is applied instead of active enable. The following table shows the state table of SR flip-flop.

<img width="703" height="388" alt="Screenshot 2025-12-13 190010" src="https://github.com/user-attachments/assets/2e0f7b70-6e0d-45ac-bd47-4fd84c54e87c" />

Here, Qtt & Qt+1t+1 are present state & next state respectively. So, SR flip-flop can be used for one of these three functions such as Hold, Reset & Set based on the input conditions, when positive transition of clock signal is applied. The following table shows the characteristic table of SR flip-flop. Present Inputs Present State Next State

<img width="617" height="523" alt="Screenshot 2025-12-13 190020" src="https://github.com/user-attachments/assets/9d768077-d23d-4c14-8275-f355d9282003" />

By using three variable K-Map, we can get the simplified expression for next state, Qt+1t+1. The three variable K-Map for next state, Qt+1t+1 is shown in the following figure.

<img width="342" height="263" alt="Screenshot 2025-12-13 190033" src="https://github.com/user-attachments/assets/ba0650ed-a728-490d-914e-ef819562762f" />

The maximum possible groupings of adjacent ones are already shown in the figure. Therefore, the simplified expression for next state Qt+1t+1 is Q(t+1)=S+R′Q(t)Q(t+1)=S+R′Q(t)

PROGRAM:

```
module sr_flip_flop (
    input  wire clk, rst, S, R,
    output reg  Q
);
    always @(posedge clk) begin
        if (rst)
            Q <= 1'b0;         // Reset
        else begin
            case ({S,R})
                2'b00: Q <= Q;     // No change
                2'b01: Q <= 1'b0;  // Reset
                2'b10: Q <= 1'b1;  // Set
                2'b11: Q <= 1'bx;  // Invalid
            endcase
        end
    end
endmodule
 F
```
RTL LOGIC FOR FLIPFLOP:
[EX 06 Dia.pdf](https://github.com/user-attachments/files/24142777/EX.06.Dia.pdf)

wave form sr  flip flop :
<img width="1179" height="771" alt="Screenshot 2025-12-13 211717" src="https://github.com/user-attachments/assets/022ac8eb-af15-470e-b417-a95d91d97c98" />

