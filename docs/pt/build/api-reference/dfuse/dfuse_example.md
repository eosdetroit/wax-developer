---
title: Exemplo do dfuse
order: 121
---

# Exemplo do dfuse

Neste exemplo, nós vamos nos registrar em uma conta gratuita e pegar o abi da WAX RNG usando uma chamada REST do dfuse.

1. Cadastre-se em uma <a href="https://dfuse.eosnation.io/" target="_blank">conta gratuita dfuse</a>.

2. Clique em __Create New Key__ (Criar uma nova chave).

3. Obtenha um token JWT de curta duração utilizando sua chave da API.

```
  curl -X POST \
  https://auth.eosnation.io/v1/auth/issue \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -d '{
	"api_key": "server_00d11abcd7e68f999d850c8efc6ab99"
}'
```

4. Use o endpoint `abi` para obter o endpoint do WAX RNG smart contract. No cabeçalho, modifique a Authorization para Bearer e use seu JWT do passo anterior.

```
    curl -X GET \
      'https://wax.dfuse.eosnation.io/v0/state/abi?account=orng.wax&json=true' \
      -H 'Authorization: Bearer Your.JWT.Token' \
      -H 'cache-control: no-cache'
```

### Exemplo de Resposta

```json
    {
    "block_num": 9135393,
    "account": "orng.wax",
    "abi": {
        "version": "eosio::abi/1.1",
        "structs": [
            {
                "name": "config_a",
                "base": "",
                "fields": [
                    {
                        "name": "name",
                        "type": "uint64"
                    },
                    {
                        "name": "value",
                        "type": "int64"
                    }
                ]
            },
            {
                "name": "jobs_a",
                "base": "",
                "fields": [
                    {
                        "name": "id",
                        "type": "uint64"
                    },
                    {
                        "name": "assoc_id",
                        "type": "uint64"
                    },
                    {
                        "name": "signing_value",
                        "type": "uint64"
                    },
                    {
                        "name": "caller",
                        "type": "name"
                    }
                ]
            },
            {
                "name": "killjobs",
                "base": "",
                "fields": [
                    {
                        "name": "job_ids",
                        "type": "uint64[]"
                    }
                ]
            },
            {
                "name": "pause",
                "base": "",
                "fields": [
                    {
                        "name": "paused",
                        "type": "bool"
                    }
                ]
            },
            {
                "name": "requestrand",
                "base": "",
                "fields": [
                    {
                        "name": "assoc_id",
                        "type": "uint64"
                    },
                    {
                        "name": "signing_value",
                        "type": "uint64"
                    },
                    {
                        "name": "caller",
                        "type": "name"
                    }
                ]
            },
            {
                "name": "setrand",
                "base": "",
                "fields": [
                    {
                        "name": "job_id",
                        "type": "uint64"
                    },
                    {
                        "name": "random_value",
                        "type": "string"
                    }
                ]
            },
            {
                "name": "setsigpubkey",
                "base": "",
                "fields": [
                    {
                        "name": "exponent",
                        "type": "string"
                    },
                    {
                        "name": "modulus",
                        "type": "string"
                    }
                ]
            },
            {
                "name": "signvals_a",
                "base": "",
                "fields": [
                    {
                        "name": "signing_value",
                        "type": "uint64"
                    }
                ]
            },
            {
                "name": "sigpubkey_a",
                "base": "",
                "fields": [
                    {
                        "name": "id",
                        "type": "uint64"
                    },
                    {
                        "name": "exponent",
                        "type": "string"
                    },
                    {
                        "name": "modulus",
                        "type": "string"
                    }
                ]
            },
            {
                "name": "version",
                "base": ""
            }
        ],
        "actions": [
            {
                "name": "killjobs",
                "type": "killjobs",
                "ricardian_contract": ""
            },
            {
                "name": "pause",
                "type": "pause",
                "ricardian_contract": ""
            },
            {
                "name": "requestrand",
                "type": "requestrand",
                "ricardian_contract": ""
            },
            {
                "name": "setrand",
                "type": "setrand",
                "ricardian_contract": ""
            },
            {
                "name": "setsigpubkey",
                "type": "setsigpubkey",
                "ricardian_contract": ""
            },
            {
                "name": "version",
                "type": "version",
                "ricardian_contract": ""
            }
        ],
        "tables": [
            {
                "name": "config.a",
                "index_type": "i64",
                "type": "config_a"
            },
            {
                "name": "jobs.a",
                "index_type": "i64",
                "type": "jobs_a"
            },
            {
                "name": "signvals.a",
                "index_type": "i64",
                "type": "signvals_a"
            },
            {
                "name": "sigpubkey.a",
                "index_type": "i64",
                "type": "sigpubkey_a"
            }
        ]
    }
}
```
