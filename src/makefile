#
# �Ȃ̂�mini�ɂ���Ƃ���NANOHAMINI=1�̑O��#�����A
# �Ȃ̂�nano�ɂ���Ƃ���NANOHAMINI=1�̑O��#��t���ANANOHANANO=1�̑O��#�����
# nanopery�ɂ���Ƃ���NANOPERY=1�̑O��#�����
#
#NANOHAMINI=1
#NANOHANANO=1

EVAL_TYPE=EVAL_APERY
EVAL_OBJ=evaluate_apery.o
EXE = usapyon2dashAVX
PGD = usapyon2dashAVX.pgd
PGOLOG = usapyon2dashAVX_prof.txt

OBJS = mate1ply.o misc.o timeman.o $(EVAL_OBJ) position.o \
	 tt.o main.o move.o \
	 movegen.o search.o uci.o movepick.o thread.o ucioption.o \
	 benchmark.o book.o \
	 shogi.o mate.o problem.o

CC=g++
LD=link



# Compile Options
#
# -DEVAL_MINI      �Ȃ̂�mini(2��֌W(KP+PP)�̕]���֐�)
# -DEVAL_NANO      �Ȃ̂�nano(2��֌W(KP�̂�)�̕]���֐�)
# -DEVAL_APERY     nanopery(Apery�̕]���֐�)
#
# -DTWIG           Apery(����̎})�̕]���֐����g��
# -DUSE_AVX2_EVAL  �]���֐��̌v�Z����AVX���߂��g��
#
# Visual C++�I�v�V����
#
# /D_CRT_SECURE_NO_WARNINGS
#                   secure�Ȋ֐����g���Ă��Ȃ��Ƃ��̌x�����o���Ȃ�
# /Zc:forScope      �X�R�[�v ���[�v�ɕW�� C++ ��K�p����
# /Wall             �x�������ׂėL���ɂ���
# /GS[-]            �Z�L�����e�B �`�F�b�N��L���ɂ���
# /favor:<blend|AMD64|EM64T> �œK������v���Z�b�T
# /GL[-]            �����N���̃R�[�h�������s��
# /RTCs             �X�^�b�N �t���[�� �����^�C�� �`�F�b�N
# /RTCu             ����������Ă��Ȃ����[�J���ϐ��̃`�F�b�N

FLAGS = -DNDEBUG -D$(EVAL_TYPE) -DUSAPYON2 -DNANOHA -DCHK_PERFORM -DTWIG -DUSE_AVX2_EVAL\
	-DOLD_LOCKS \
	 
#CXXFLAGS=$(FLAGS) /MT /W4 /Wall /nologo /Od /GS /RTCsu
CXXFLAGS=$(FLAGS) -O3 -DIS_64BIT -msse -std=c++11 -mavx2 -Wa,-q -c
LDFLAGS=-lpthread -o$(EXE)
PGOLDFLAGS1=/NOLOGO /STACK:16777216,32768 /out:$(EXE) /LTCG:PGI
PGOLDFLAGS2=/NOLOGO /STACK:16777216,32768 /out:$(EXE) /LTCG:PGO


all: $(EXE)

$(EXE) : $(OBJS)
	$(CC) -o $@ $(OBJS) $(LDFLAGS)

.cpp.o :
	$(CC) $(CXXFLAGS) $*.cpp

clean :
	rm -f *.o
	rm -f    $(EXE)
