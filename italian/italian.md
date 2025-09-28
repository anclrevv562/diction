CONTINUE
=====

=====

TO-REREAD
=======================
pg.10 dieresis
pg.13 syllables
pg.15 apocopation
pg.20-21 vowel length
pg. 21 cons pron.
pg.25 intervocalic s
pg.27-28 zz
pg.29 c/g
======================

CONCERNS
======================
COMPOUND WORDS MARKER?
IF FOLLOWING CHAR IS MODIFIED BEFORE, DO I NEED A RERUN THE LOOP?
DEALING WITH H AND WHEN FIELDS MATTER BUT CONTENT IS EMPTY
==================================================================

PROPERTIES
=========================
word.syllable = int

char.consonant = bool
char.vowel = bool
char.voiced = bool
char.vowel.stress = bool
char.vowel.accent_grave = bool
char.lemoner = bool
char.length = bool
char.glide = bool
char.hardness = soft / hard / none?
=========================

CONSONANT/VOWEL DESIGNATOR
====================================================
Consonants = [b,c,d,f,g,h,l,m,n,p,m,n,p,q,r,s,t,v,z]
Vowels = [a,à,e,è,é,i,ì,í,î,o,ò,ó,ô,u,ù,ú]
Diphthongs = [ae,ai,ao,au,ea,ei,eo,ia,ie,io,iu,oa,oe,oi,ou,ua,ue,ui,uo]
Triphthongs = !!!pg.18-19!!!
Lemoners = [l,m,n,r,s(sometimes)] if WI not Lemoner !!!pg.11!!!
Prefix = [XX,XX] !!!pg.12!!!
Consonant_Cluster = [XXX] !!!pg.13!!!
===============================================================

SYLLABIFICATION RULES
======================
single_consonant = V-V
double_consonant = C-C(same)
consonant_cluster = if lemoner, L-L+
    -if -sci-, -sce, -gn-, -gl-:
        -don't make consonant_cluster
    -EXCEPTIONS tecnica, abdicare
        -normal rules
!!!pg.12 r!!!
a
-if _V-
    -_-V

e
-if _V-
    -_-V

i
-if V_V:
    V-_V

o
-if _V'
    -_-V
==================================

STRESS RULES
==================================
if syllable >= 2:
    -penultimate has stress !!!parola piana!!!
if syllable >= 3:
    -antepenultimate has stres !!!parola sdrucciola!!!
if syllables >= 4:
    -fourth to last has stress !!!parola bisdrucciola!!!
sometimes if accent_grave == True or accent_acute = True:
    -stress
==================================

VOWEL RULES
==============================================================
ɑ
(brighter than English)
(towards hard palate, with soft palate raised)
(spread, bright)
-if ɑ:
    -/a/

e
-if e:
    -/e/ or /ɛ/

i
-if c_V, g_V, sc_V, gl_V
    -/NONE/
-if FINAL STRESS _a, _e, _o:
    -/i/
-if i:
    -/i/ or /j/
-if syllable == 1 and C_u and u.accent_grave == True: !!!CHECK!!!
    -/j/
-if V_V:
    -/j/
-if syllable == 1 and C_a and a.accent_grave == True: !!!CHECK!!!
    -/ʒ/
-if syllable == 1 and C_o and o.accent_grave == True: !!!CHECK!!!
    -/ʃ/
-if ii:
    -/i/


ì
-if syllable == 2 and _V
    -/ia/ diphthong !!!CHECK!!!

î
-if î:
    -/i/

o
-if o:
    -/o/ or /ɔ/

ô
-if ô:
    -/o/

u
-if u:
    -/u/ or /w/
-if syllable == 1 and C_V and V(WF).accent_grave == True:
    -/w/
==============================================================

CONSONANT RULES
==========================
b
-if b:
    -/b/

c
-if _a, _o, _u, _C (not -gli and -g):
    -/k/
-if _i, _e:
    -/tʃ/
if _c or c_:
    -/kk/
if _h:
    -/k/

d
-if d:
    -/d/

f
-if f:
    -/f/

g
-if _a, _o, _u, _C (not -gli and -g):
    -/g/
-if _i, _e:
    -/dʒ/
-if g_ or _g:
    /gg/
-if _h:
    -/g/    
    
h
-NONE

l
-if l:
    -/l/

m
-if m:
    -/m/

n
-if n:
    -/n/

p
-if p:
    -/p/

r
-if V_V:
    -/ɾ/
-if _r or r_:
    -/r/
-if _CC:
    -/r/
if CC_:
    -/r/
if WI_:
    -/r/
if _WF:
    -/r/

s
if WI_V:
    -/s/
if _unvoicedC:
    -/s/
if C_:
    -/s/
if _s or s_:
    -/s/
if _WF:
    -/s/
if _voicedC:
    -/z/
if V_V:
    -_i and verb:
        -/s/
    -ri_V, di_V, tra_V:
        -/s/
    -pre_:
        -/s/
    -COMPOUND WORD()
    -else /z/

t
-if t:
    -/t/

v
-if v:
    -/v/

z
-if V_i(glide):
    -/s/ [AZIENDA is exception]
-if V_V:
    -/z/
-if WI_:
    -/z/ OFTEN
    -/s/ SOMETIMES (REGIONAL)
-if _n:
    -/ts/ OFTEN
    -/dz/ SOMETIMES
-if _l:
    -/s/
-if _r:
    -/s/ OFTEN
    -/s/ SOMETIMES
-if _z or z_:
    -
