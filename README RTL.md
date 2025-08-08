```verilog
module t_ff_sync_rst_n( input wire t,clk,rst_n,
                       output reg q,
                       output wire q_bar);
  //always @ (posedge clk or negedge rst_n); - Asynchronous
  always @ (posedge clk) begin
  if (rst_n ==0)
    q <= 0;
  else 
    q <= (t ? ~q: q);
  end
  
  assign q_bar = ~q;
endmodule
