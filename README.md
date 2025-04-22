![](AFD.jpeg)
# AFD_LOGIN
### 📦 Conjunto de Estados (Q)

Q = { q0, q1, q2, q3, q4, q5, q6 }

- `q0`: Início (usuário não autenticado)
- `q1`: Login em andamento (credenciais enviadas)
- `q2`: Autenticado (Access Token válido)
- `q3`: Access Token expirado
- `q4`: Refresh Token falhou (deve logar novamente)
- `q5`: Novo Access Token gerado com sucesso
- `q6`: Falha definitiva (login ou refresh inválido)

---

### 🔡 Alfabeto de Entrada (Σ)

Σ = { start_login, login_ok, login_fail, token_expired, refresh_ok, refresh_fail, new_token }

- `start_login`: Ação de iniciar o login
- `login_ok`: Credenciais válidas
- `login_fail`: Credenciais inválidas
- `token_expired`: Access Token expirou
- `refresh_ok`: Refresh Token válido
- `refresh_fail`: Refresh Token inválido ou expirado
- `new_token`: Novo Access Token foi gerado

---

### 🔁 Função de Transição (δ)

A função δ: Q × Σ → Q define as transições entre estados. Abaixo estão as transições do autômato:

- δ(q0, start_login) → q1
- δ(q1, login_ok) → q2
- δ(q1, login_fail) → q6
- δ(q2, token_expired) → q3
- δ(q3, refresh_ok) → q5
- δ(q3, refresh_fail) → q4
- δ(q4, start_login) → q1
- δ(q5, new_token) → q2
