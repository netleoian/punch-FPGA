module finalPRO(RESET,push,HEX0,HEX1,HEX2,HEX3,Begin,hard,clk,LEDG,point);
input RESET;
input push;
output [6:0]HEX0;
output [6:0]HEX1;
output [6:0]HEX2;
output [6:0]HEX3;
reg[3:0]scoredigital;//計分
reg[3:0]scoreten;
output reg [9:0]LEDG=10'b0000011011; 
input Begin;
input hard;
input clk;
reg [26:0]clkcount;
reg clk2;
reg seed;
reg [3:0]seconddigital=4'b0000;
reg [3:0]secondten=4'b0101;
reg second;
output reg point=1'b0;
reg timeout=1'b1;
always@(posedge clk)begin//CLK
clkcount<=clkcount+1'b1;
if(hard)
clk2<=clkcount[21];
if(!hard)
clk2<=clkcount[22];

second<=clkcount[24];
end
always@(posedge second)begin//時間秒數
	if(RESET)begin
	seconddigital=4'b0001;
	secondten=4'b0101;
	timeout=1'b1;
	end
	if(Begin)begin
	if(seconddigital!=4'b0000)
		seconddigital=seconddigital-1'b1;
	else begin
		if(secondten!=4'b0000)begin
		 secondten=secondten-1'b1;
		 seconddigital=4'b1001;
		 end
		 else begin
		 timeout=1'b0;
		 end
	end
	end
end

always@(posedge clk2)begin
if(RESET)//重製
LEDG=10'b0000011011;

seed=!seed;
if(Begin&& timeout)begin//LED亮燈和產生
	LEDG[9]<=LEDG[8];
	LEDG[8]<=LEDG[7];
	LEDG[7]<=LEDG[6];
	LEDG[6]<=LEDG[5];
	LEDG[5]<=LEDG[4];
	LEDG[4]<=LEDG[3];
	LEDG[3]<=LEDG[2];
	LEDG[2]<=LEDG[1];
	LEDG[1]<=LEDG[0];
	LEDG[0]<=(LEDG[9]^LEDG[8]^LEDG[5]^LEDG[3]);
end
end
always@(posedge clk2)begin//計分

	if(RESET)begin//重製
	scoredigital=4'b0000;
	scoreten=4'b0000;	
	end
	
	if(Begin&& timeout) begin	
		if(LEDG[9] && !push)begin//有正確擊中
			if(scoredigital==4'b1001)begin
			scoreten=scoreten+1'b1;
		scoredigital=4'b0000;
			end
			else begin
			scoredigital=scoredigital+1'b1;
			end
		end
		if(LEDG[9] && push || !LEDG[9] && !push)begin//擊錯 或 沒打
			if(scoredigital==4'b0000)begin
			if(scoreten!=4'b0000)begin
			scoreten=scoreten-1'b1;
			scoredigital=4'b1001;
			end
			end
			else begin
			scoredigital=scoredigital-1'b1;
			end
		end
	end
end
//顯示
out(.a(secondten),.HEX(HEX3));
out(.a(seconddigital),.HEX(HEX2));
out(.a(scoreten),.HEX(HEX1));
out(.a(scoredigital),.HEX(HEX0));
endmodule
