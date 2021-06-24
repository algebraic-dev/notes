# SIMD

Registradores de vetores guardam 4 (SSE) ou 8 (AVX) escalares.

## Exemplo
Usando 4 dados de onde cada um corresponde a um *player* diferente para calcular a velocidade dos players pelo teorema de pitágoras, podemos calcular de maneira normal:

```glsl
for( int i = 0; i < 4; i++ ){
	vec3 velocity = GetPlayerSpeed();
	float length = velocity.Length();
}
```

Ou utilizando um design com SIMD (Com Data-Oriented Design)

```glsl
x4 = GetPlayerXSpeeds();
y4 = GetPlayerYSpeeds();
z4 = GetPlayerZSpeeds();
x4squared = x4 \* x4;
y4squared = y4 \* y4;
z4squared = z4 \* z4;
sum4 = x4squared + y4squared;
sum4 = sum4 + z4squared;
length4 = sqrtf4( sum4 )
```

