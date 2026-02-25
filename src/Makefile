# Intel ifx makefile

FC := ifx
FFLAGS := -r8 -O3 -axCORE-AVX2,CORE-AVX512 -mprefer-vector-width=512 -qopt-zmm-usage=high -qopenmp
LDFLAGS := -static-intel -qopenmp -qopenmp-link=static -qmkl

# FFLAGS := -r8 -O3 -axCORE-AVX2,CORE-AVX512 -mprefer-vector-width=512 -qopt-zmm-usage=high
# LDFLAGS := -static # pure static doesn't work here


OBJ := \
constants.o\
model_mod.o\
ttm2f_mod.o\
ttm3f_mod.o\
nasa_mod.o\
math.o\
smear.o\
nasa.o\
potential_mod.o\
bemsa2b.o\
bemsa3b.o\
bemsa4b.o\
pes_shell.o\

OBJPOT := \
getpot.o


%.o : %.f90
	$(FC) -c $(FFLAGS) $< 

getpot.x :  $(OBJ) $(OBJPOT)
	$(FC) -o $@  $^ $(LDFLAGS)

clean :
	rm *.o *.mod
