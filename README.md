# Water-Level-Indicator
  The "Water Level Indicator " project aims to develop an automated solution for effective  water management, targeting issues such as water overflow, dry running of pumps, and water  wastage. 
      Code :
      
      module wle2( 
        input [8:0] lv, 
        output reg [3:0] BCD, 
        output reg [6:0] seg 
      ); 
      always @(*) begin 
        casex(lv) 
            9'b1xxxxxxxx : BCD = 4'b1001; 
            9'b01xxxxxxx   : BCD = 4'b1000; 
            9'b001xxxxxx   : BCD = 4'b0111; 
            9'b0001xxxxx   : BCD = 4'b0110; 
            9'b00001xxxx  : BCD = 4'b0101; 
            9'b000001xxx  : BCD = 4'b0100; 
            9'b0000001xx : BCD = 4'b0011; 
            9'b00000001x   : BCD = 4'b0010; 
            9'b000000001   : BCD = 4'b0001; 
            9'b000000000   : BCD = 4'b0000; 
            default: BCD = 4'b1111;  
        endcase 
    end 
     
    always @(*) begin 
        case(BCD) 
            4'b0000 : seg = 7'b0000001; 
            4'b0001 : seg = 7'b1001111; 
            4'b0010 : seg = 7'b0010010; 
            4'b0011 : seg = 7'b0000110; 
            4'b0100 : seg = 7'b1001100; 
            4'b0101 : seg = 7'b0100100; 
            4'b0110 : seg = 7'b0100000; 
            4'b0111 : seg = 7'b0001111; 
            4'b1000 : seg = 7'b0000000; 
            4'b1001 : seg = 7'b0000100; 
            default: seg = 7'b1111111;  
        endcase  
        end 
      endmodule 
___________
