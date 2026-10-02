面向对象和面向过程本质是一个**认识论**的问题，而不是编程领域特有的两种编程思想。因为本质上编程是将现实世界投影到编程空间中，这个问题可以追溯到亚里士多德：您把这个世界视为过程还是对象？

怎么理解这两种认识的差异呢？

面向对象和面向过程所关注的**重点**或者说**实体**是不一样的。

面向过程主要在想“要做什么事情”

而面向对象则在考虑“谁负责做这件事情”

比如我们实现一个游戏，里面有玩家，然后我们要实现玩家的移动、攻击、受伤和回血效果。

在**面向过程**中，我们会很自然的写成：

```cpp
struct Player {
    int hp;
    int x;
    int y;
    int attack;
};

void move(Player* player, int dx, int dy);
void attack(Player* player, Enemy* enemy);
void take_damage(Player* player, int damage);
void heal(Player* player, int amount);
```

注意这里我们主要在想的是我们要实现玩家的移动、攻击、受伤和回血效果，所以就会专注于实现移动、攻击、受伤和回血这几个方法，然后只要我们传入玩家，就可以直接修改玩家的某些属性来完成这些事情。

它的思维通常倾向于将数据和处理数据的过程分别组织：

```
数据：
Player

过程：
move()
attack()
take_damage()
heal()
```

如果我们用面向对象来实现的话，就会实现成这样：

```cpp
class Player {
private:
    int hp;
    int x;
    int y;
    int attack_power;

public:
    void move(int dx, int dy);
    void attack(Enemy& enemy);
    void takeDamage(int damage);
    void heal(int amount);
};
```

它的思维是：Player 是一个东西。 这个东西： 有自己的状态 知道自己能做什么 自己维护自己的状态

|面向过程|面向对象|
|---|---|
|重点通常是“要完成什么过程”|重点通常是“谁负责完成这个行为”|
|`attack(player, enemy)`|`player.attack(enemy)`|
|数据与处理数据的过程倾向于分别组织|状态与维护状态的行为倾向于组织在一起|
|常按步骤、功能、过程拆分|常按对象、职责、协作关系拆分|
|核心抽象往往是函数/过程|核心抽象往往是对象/消息/接口|
