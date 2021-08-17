# 카드플레이어 출력하기-
## 개요
  조건에 맞춰 카드 게임을 플레이 하고 승자를 출력하는 문제입니다.
  1. 플레이어의 수를 입력 받습니다. 플레이어는 최소 플레이어어의 이름과 점수를 가질 수 있어야 합니다.
  2. 플레이어의 수를 입력 후 카드의 갯수도 입력 받습니다. 
  3. 입력된 갯수의 카드만큼이 플레이어에게 분배됩니다. 카드의 숫자는 중복될 수 있습니다.
  4. 카드가 분배되면 카드 점수의 합을 계산해서 승자를 뽑습니다. 점수의 합이 같을경우 후순위 플레이어가 승자가 됩니다.
  5. 프로그램 종료시 승리한 플레이어의 이름과 카드 리스트, 점수의 합을 [출력 예]와 같이 출력하고 종료합니다.


```javascript

// 카드 숫자를 생성한다
function getCardNumber() {
  // 카드는 1~20 사이의 임의의 숫자
  const randomNumber = Math.floor(Math.random() * (20 - 1))
  return randomNumber
}

// 카드 플레이어를 생성한다.
const player1 = []
const player2 = []
const player3 = []

// 각 플레이어에 카드를 나눠준다.
function setCardNumberToPlayer(cardCount) {
// 코드를 구현한다
}

// 각 플레이어의 카드합을 게산해서 승리자를 확인하여 출력한다.
// 점수가 동일할경우 나중 플레이어가 이긴것으로 한다.
function getWinner() {
// 코드를 구현한다.
}

// 카드 게임을 시작한다.
async function init() {
  // 카드의 갯수는 3개로 지정한다.
  const cardCount = 3
  await setCardNumberToPlayer(cardCount)
  await getWinner()
  // 카드게임의 승자를 구한다.

}

init()


```

## 출제의도
1. 함수형 구현에 대해 알고 있는지 확인합니다.
2. 오브젝트 및 배열을 다루는 법을 확인합니다.
3. ES6의 화살표 함수 및 배열 함수에 대해 아는지 확인합니다.

## 채점기준
1. 필요한 부분은 배열 함수 형태로 바로 처리하는지 확인합니다.
2. 펑션을 생성하지 않고 화살표 함수로 만드는지 확인합니다.
3. 데이터를 나누고 처리하는 방법을 확인합니다.
4. 프로그램을 구동 했을때 답안이 출제 설명과 같은지 확인합니다.

## 답안 유형
player2 42

```javascript
function getCardNumber() {
  return Math.floor(Math.random() * (20 - 1))
}

const playerList = [
  {
    name: 'player1',
    score: []
  },
  {
    name: 'player2',
    score: []
  },
  {
    name: 'player3',
    score: []
  }
]

function setCardNumberToPlayer(cardCount) {
  let cnt = 0
  while (cnt < cardCount) {
    playerList.map(({ score }) => score.push(getCardNumber()))
    cnt++
  }
}

function getWinner() {
  let maxPlayer = ''
  let maxNumber = 0
  playerList.forEach(item => {
    const playerValue = getPlayerSum(item.score)
    if (maxNumber <= playerValue) {
      maxNumber = playerValue
      maxPlayer = item.name
    }
  })
  console.log(maxPlayer, maxNumber)
}

function getPlayerSum(player) {
  return player.reduce((sum, current) => sum + current, 0)
}

async function init() {
  const cardCount = 3
  await setCardNumberToPlayer(cardCount)
  await getWinner()
}

init()

```
