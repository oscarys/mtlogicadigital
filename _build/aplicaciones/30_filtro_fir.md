---
redirect_from:
  - "aplicaciones/30-filtro-fir"
interact_link: content/aplicaciones/30_filtro_fir.ipynb
kernel_name: python3
has_widgets: false
title: 'Filtro digital FIR'
prev_page:
  url: /aplicaciones/20_comparador_magnitud.html
  title: 'Comparador de magnitud'
next_page:
  url: /aplicaciones/40_alu.html
  title: 'Unidad lógica-aritmética'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---
# **Filtro digital FIR**



```vhdl
library ieee;
  use ieee.std_logic_1164.all;
  use ieee.numeric_std.all;
use work.types.all;

library maths;
  use maths.maths_class.all;
library matrix;
  use matrix.matrix_class.all;

entity FIR_32tap_8_8 is
port (
  a : in  std_logic_vector(7 downto 0);
  b : in  logic_8_vector(31 downto 0);
  clock : in  std_logic;
  reset : in  std_logic;
  y : out std_logic_vector(20 downto 0)
);
end FIR_32tap_8_8;

architecture behavioural of FIR_32tap_8_8 is

  constant number_of_taps: integer := 32;

  signal data_table: single_vector(number_of_taps-1 downto 0);
  signal coefficient_table: single_vector(number_of_taps-1 downto 0);

begin

  -- y <= sum_over (0, k-1, a((k-1)-i), b(i))
  -- coefficient_table <= b;

  fir_algorithm: process (clock)
    variable data_out : single;
    variable fir_result : single;
    variable data_table_var: single_vector(number_of_taps-1 downto 0);
    -- the coeff table assignment really ought to be handled at the entity interface
    variable coefficient_table_var: single_vector(number_of_taps-1 downto 0);
    variable tmp : single_vector(number_of_taps-1 downto 0);
    variable tmp2 : single;
    variable tmp3 : single_vector(number_of_taps-1 downto 0);
    variable tmp4 : integer;
    variable num_taps_minus_1 : integer;
    variable y_result : signed(20 downto 0);
  begin
    if rising_edge(clock) then
      -- data_table_var := data_table(number_of_taps-1) & data_table(number_of_taps-2 downto 0);
      -- putting the coeff table in a loop like this allows dynamic coeff updating
      for i in 0 to number_of_taps-1 loop
        coefficient_table_var(i) := single(to_integer(unsigned(b(i))))/127.0;
      end loop;
      -- tmp := reverse_order(data_table_var);

      -- tmp2 := 0.15;  + to_integer(a);
      data_table_var := data_table;
      tmp2 := single(to_integer(signed(a)));
      data_table_var := shift_fifo (data_table_var, tmp2); -- fifo =>  data_in =>
      data_table <= data_table_var;

      -- tmp3 := reverse_order(data_table_var);
      -- tmp4 := 0;
      num_taps_minus_1 := number_of_taps-1;
      fir_result := sum_of_products (
        lower_limit => 0,
        upper_limit => number_of_taps-1,
        a_in => reverse_order(data_table_var),
        b_in => coefficient_table_var
      );
      y_result := to_signed(integer(fir_result), y_result'length); -- this causes an array bug to_std_logic_vector(
      y <= std_logic_vector(y_result); -- this causes an array bug  -- to_twos_complement
    end if;
  end process;

end behavioural;
```

