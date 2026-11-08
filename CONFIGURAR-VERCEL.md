# Configuração Vercel — VIVA BLACKCAT

Em Project > Settings > Environment Variables, configure:

- `BLACKCAT_API_KEY`: chave **nova** da sua conta BlackCat (não coloque no GitHub).
- `UPSTASH_REDIS_REST_URL`: URL REST do banco Upstash Redis.
- `UPSTASH_REDIS_REST_TOKEN`: token REST do mesmo banco.

Faça Redeploy após salvar. O painel usa `/admin.html` e `/api/fichas`. A confirmação de fichas pagas agora consulta `/sales/{transaction_id}/status` na BlackCat, exigindo retorno `PAID`.

**Segurança:** a chave BlackCat estava exposta no ZIP anterior; revogue-a e gere outra. O painel ainda utiliza uma senha fixa no código, que deve ser substituída antes de operar com dados reais. Não coloque CPF ou dados de clientes em logs públicos.

**Teste:** crie um cadastro fictício em ambiente controlado e confirme que a ficha aparece; teste pagamento real de baixo valor somente quando as credenciais e o Redis estiverem configurados. Não houve teste online da BlackCat ou Upstash nesta revisão.
