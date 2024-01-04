# Big guides

## Testes

- n ter teste de integração

- fazer testes automáticos a cada componente sem fazer pedidos à API 

- fazer serviço fake

- usar mockk

- testar o viewModel com serviços fake.

- testar o screen com o que é suposto aparecer no ambito inicial etc.

- Screen testar com tag e com os dados que o ecra deve mostrar com cada caso (ex. passar jogo com sucesso e com insucesso) e verificar que nas tags estão ou não visíveis.

## Estado

- Separar estados da activity (dentro do VM) numa closed hierarchy com os diferentes estados

- Podemos no limite separar cada estado em diferentes ecrãs

- ver LoadState do professor

### Global state of the app

User login state, username and userId.

### Diferentes activities e diferentes estados do mesmo:

#### Login

- Edit
- Submiting
- Submited

#### About

#### Ranking (ruleId, usernameFilter)

- Loading
- Loaded

#### RankingParcial (just one user)

#### Me

- Loading
- Loaded

#### Lobby matching (quickplay only for now, if there is lobby join, if there is not choose rule and play)

- Loading
- Loaded

#### Rule selecting

- Loading
- Loaded

#### Game(gameId)

- Loading - spinner
- My turn( can click on active cells)
- Opponent turn (polling with no clicks and low gradience)
- Finished (display different content)

## Comunicação com a API

Serviço é algo que é passado ao viewmodel e que o viewmodel usa para fazer pedidos à API.

Para este efeito vamos usar OkHttp e Gson.

Fazer resposta de forma sincrona com o OkHttp usa-se o método execute.
Para fazer de forma assincrona usa-se o método enqueue.

## Gestão de estado p2

- **Dependency Container** - de modo a conseguir fazer facilmente fakes de serviços, vamos usar um dependency container.

- Como fazer para no ecrã de ranking ao clicar num utilizador ir para o ecrã de ranking parcial desse utilizador?

```kotlin
onUserSelected = { user -> RankingParcialActivity.navigate(this, user) }
```

No navigate do intent o que passamos no intent segue o contrato de Parcelable. logo deve ser assim:

```kotlin
companion object {
    fun navigate(activity: Activity, user: User) {
        val intent = Intent(activity, RankingParcialActivity::class.java)
        intent.putExtra(USER_EXTRA, UserExtra(user))
        activity.startActivity(intent)
    }
}
@Parcelize
data class UserExtra(val rank: Int, val username: String, val score: Int) : Parcelable {
    constructor(user: User) : this(user.rank, user.username, user.score)
}

private fun JokeExtra.toJoke() = Joke(rank, username, score)
```

Ver JokeDisplayActivity no projeto de exemplo.

- Usar value class se der, uma value class tem apenas um campo imutável e escusamos de escrever .value para aceder ao valor. 

- N usar LazyColumn e LazyRow quando o conteudo é estático e sabemos tamanho.


Testes ao vm são fáceis e explicados na aula 08 Gestão de estado (parte 2) minuto 45.

