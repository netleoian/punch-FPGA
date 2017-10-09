module out(a,HEX);
input [4:0]a;
output reg[6:0]HEX;
always@(*)begin
case(a)
	4'b0000:begin
	HEX=7'b1000000;//0
	end
	4'b0001:begin
	HEX=7'b1111001;//1
	end
	4'b0010:begin
	HEX=7'b0100100;//2
	end
	4'b0011:begin
	HEX=7'b0110000;//3
	end
	4'b0100:begin
	HEX=7'b0011001;//4
	end
	4'b0101:begin
	HEX=7'b0010010;//5
	end
	4'b0110:begin
	HEX=7'b0000010;//6
	end
	4'b0111:begin
	HEX=7'b1011000;//7
	end
	4'b1000:begin
	HEX=7'b0000000;//8
	end
	4'b1001:begin
	HEX=7'b0010000;//9
	end
endcase
end

endmodule
