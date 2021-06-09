# VHDL-LUT5in1
LUT5*1


    library IEEE;
    use IEEE.STD_LOGIC_1164.ALL;
    --use WORK.row.ALL; 	
    --use ieee.numeric_std.all;
    --use ieee.std_logic_unsigned.all;
    --use IEEE.STD_LOGIC_ARITH.ALL;
    ----------------------------------------------------------------------------------
    entity LUT is
	    PORT(	A, B, C, D, E: in std_logic;
			F : in std_logic_vector(0 downto 31);
			LUT : out std_logic );
    end LUT;
    ----------------------------------------------------------------------------------
    architecture Behavioral of LUT is

    begin

	LUT <= (F(0) and (not(A) and not(B) and not(C) and not(D) and not(E))) or 
	(F(1) and (not(A) and not(B) and not(C) and not(D) and E)) or
	(F(2) and (not(A) and not(B) and not(C) and D and not(E))) or
	(F(3) and (not(A) and not(B) and not(C) and D and E)) or
	(F(4) and (not(A) and not(B) and C and not(D) and not(E))) or
	(F(5) and (not(A) and not(B) and C and not(D) and E)) or
	(F(6) and (not(A) and not(B) and C and D and not(E))) or
	(F(7) and (not(A) and not(B) and C and D and E)) or
	(F(8) and (not(A) and B and not(C) and not(D) and not(E))) or
	(F(9) and (not(A) and B and not(C) and not(D) and E)) or
	(F(10) and (not(A) and B and not(C) and D and not(E))) or
	(F(11) and (not(A) and B and not(C) and D and E)) or
	(F(12) and (not(A) and B and C and not(D) and not(E))) or
	(F(13) and (not(A) and B and C and not(D) and E)) or
	(F(14) and (not(A) and B and C and D and not(E))) or
	(F(15) and (not(A) and B and C and D and E)) or
	(F(16) and (A and not(B) and not(C) and not(D) and not(E))) or
	(F(17) and (A and not(B) and not(C) and not(D) and E))	or
	(F(18) and (A and not(B) and not(C) and D and not(E))) or
	(F(19) and (A and not(B) and not(C) and D and E)) or
	(F(20) and (A and not(B) and C and not(D) and not(E))) or
	(F(21) and (A and not(B) and C and not(D) and E)) or
	(F(22) and (A and not(B) and C and D and not(E))) or
	(F(23) and (A and not(B) and C and D and E)) or
	(F(24) and (A and B and not(C) and not(D) and not(E))) or
	(F(25) and (A and B and not(C) and not(D) and E)) or 
	(F(26) and (A and B and not(C) and D and not(E))) or
	(F(27) and (A and B and not(C) and D and E)) or
	(F(28) and (A and B and C and not(D) and not(E))) or
	(F(29) and (A and B and C and not(D) and E)) or
	(F(30) and (A and B and C and D and not(E))) or
	(F(31) and (A and B and C and D and E)); 
	
    end Behavioral;

#TestBench

    LIBRARY ieee;
    USE ieee.std_logic_1164.ALL;
    ----------------------------------------------- 
    ENTITY LUTtest IS
    END LUTtest;
 
    ARCHITECTURE behavior OF LUTtest IS 
 
    -- Component Declaration for the Unit Under Test (UUT)
 
    COMPONENT LUT
    PORT(
         A : IN  std_logic;
         B : IN  std_logic;
         C : IN  std_logic;
         D : IN  std_logic;
         E : IN  std_logic;
         F : IN  std_logic_vector(0 to 31);
         LUT : OUT  std_logic
        );
    END COMPONENT;
    

     --Inputs
     signal A : std_logic := '0';
     signal B : std_logic := '0';
     signal C : std_logic := '0';
     signal D : std_logic := '0';
     signal E : std_logic := '0';
     signal F : std_logic_vector(0 to 31) := (others => '0');

 	--Outputs
    signal LUT : std_logic := ;
    -- No clocks detected in port list. Replace <clock> below with 
     -- appropriate port name 
 
 
    BEGIN
 
	-- Instantiate the Unit Under Test (UUT)
     uut: LUT PORT MAP (
          A => A,
          B => B,
          C => C,
          D => D,
          E => E,
          F => F,
          LUT => LUT
        );

  
     -- Stimulus process
    stim_proc: process
     begin		
      -- hold reset state for 100 ns.
      wait for 100 ns;	
		A <= '1';
		B <= '1';
		C <= '1';
		D <= '1';
		E <= '1';
		F <= "00000000000000000000000000000001";
		
      -- insert stimulus here 

      wait;
    end process;

    END;

