# Vaja7-PWM-NUCLEO

PINOUT:

<img width="684" height="637" alt="image" src="https://github.com/user-attachments/assets/c797ce05-5d2a-44e7-b30f-dfb98c0f4e40" />

IZREZEK TIM 1, Parameter Settings:

<img width="608" height="586" alt="image" src="https://github.com/user-attachments/assets/3788b6a6-a1ab-4a92-9fcd-6cc672d0f2ca" />

FOTOGRAFIJA OSCILOSKOPA

<img width="800" height="600" alt="image" src="https://github.com/user-attachments/assets/6fcc2709-aa8e-4d05-8da4-5c129047e87a" />

ODGOVORI NA VPRAŠANJA:

2.

b) Omogočili smo pin PA8, Poleg pina se izpiše TIM1_CH1.

d) Prescaler je 16.

e) Po nastavitvi Counter Period 100 znaša takt časovnika 10kHz.

f) Nastavi delovni cikelj. Delovni cikelj je razmerje med trajanjem impulza in periodo PWM signala. S tem ko pod PWM Generation Channel Pulse zapišemo vrednost 50, dosežemo 50% delavni cikelj.

3.

b) Ukaz za Pulse ki ga je generiral CubeMX: sConfigOC.Pulse= 50;

c) Inicializacija časovnika za PWM signal:
HAL_TIM_PWM_Start(&htim1, TIM_CHANNEL_1);

4.

f) T= 27 uS       Ton= 13,5 uS

5.

a)  Ukaz za spremembo širine impulza na 25%: sConfigOC.Pulse = 25;

g) 

  htim1.Instance->CCR1 = dutyCycle;
  
V register CCR1 zapišemo vrednost spremenljivke dutyCycle, s čimer neposredno določimo širino impulza (dolžino vklopa) PWM signala.

• dutyCycle += 10;

Vrednost spremenljivke dutyCycle povečamo za korak 10.

• if(dutyCycle > 90) dutyCycle = 10;

Preverimo mejno vrednost: če dutyCycle preseže 90, ga ponastavimo na začetno vrednost 10.

• HAL_Delay(1000);

Izvajanje programa zaustavimo za eno sekundo (1000 milisekund).

KOMENTAR: 

Z osciloskopom sva spremljalia generirane PWM signale mikrokrmilnika STM32. Najprej sva izmerila fiksna delovna cikla (50 % in 25 %), nato pa programirala dinamično spreminjanje širine impulza. Naslednja se je vsako sekundo stopnjevala za 10 % (v območju 10–90 % periode), po doseženi meji pa se je cikel samodejno ponastavil.
