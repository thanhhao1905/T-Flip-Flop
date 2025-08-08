```verilog
`timescale 1ns/1ps
module tb_t_ff_sync_rst_n;
  reg t,clk,rst_n;
  wire q , q_bar;
  
  t_ff_sync_rst_n DUT (t,clk,rst_n,q,q_bar);
  
  always #2 clk= ~clk;
  
  initial begin
    clk =0;
    rst_n =0;
    t =0;
    $display("Reset: %b ---> q=%b, q_bar=%b",rst_n,q,q_bar);
    
    #3 rst_n =1;
    $display("Reset: %b ---> q=%b, q_bar=%b",rst_n,q,q_bar);
    #3 drive(1);
    #3 drive(0);
    #3 rst_n =0;
    #3 drive(1);
    #3 rst_n =1;
    #3 drive(0);
    
    #5;
    $finish;
  end
  
  task drive(bit ip);
    @(posedge clk);
      t = ip;
      #1
      $display("t=%b, q=%b ,q_bar=%b",t,q,q_bar);
  endtask
  
  initial begin
    $dumpfile("dump.vcd");
    $dumpvars;
  end
endmodule
