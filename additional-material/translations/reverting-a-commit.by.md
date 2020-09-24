# Вярнуць каміт

Скасаваць абавязацельства проста азначае стварыць зусім новы дакумент, які адмяняе ўсе
змены, унесеныя ў папярэдні. Гэта як рабіць `` CTRL + Z `` `на git.

У Git пераўтварэнне палягчаецца, таму што кожны ўклад, які вы commit на свой аддалены сховішча, мае ўнікальны алфавітна-лічбавы ключ, вядомы пад назвай SHA (Secure Hash Algorithm).
Такім чынам, гэта азначае, што вы можаце вярнуць любыя абавязацельствы, пакуль у вас ёсць SHA.
Але потым, вы павінны быць асцярожныя, каб змяніць упарадкаванасць, каб не сапсаваць ваша сховішча.

Каб выбраць SHA канкрэтнага абавязацельства, якое мы хочам адмяніць, зручны быў бы часопіс усіх дасягнутых намі абавязкаў.
Каб атрымаць гэта, мы запусцім каманду:
`` `git log --oneline` ``
Адзінае выкананне каманды `` git log`` таксама дасць нам SHA (у доўгай форме)
Аднак выкарыстанне сцяга `` --oneline `` кажа git, што мы хочам, каб ён быў адлюстраваны ў сціслым (адным радку) парадку для зручнага чытання.

Першыя 7 знакаў, якія адлюстроўваюцца пры выкананні гэтай каманды, называюцца скарочаным хэшам фіксацыі.

Напрыклад, вось што я атрымліваю, калі ў гэтым рэпазітары запускаю `` git log --oneline ``:
```
389004d added spacing in title
c1b9fc1 Merge branch 'master' into tutorials
77eaafd added tutorial for reverting a commit
```

Гэта паказвае, што з дапамогай `` git log --oneline``, мы можам атрымаць спіс усіх абавязацельстваў, зробленых у сховішча, разам з першымі 7 сімваламі яго SHA.

Давайце выкажам здагадку, што я хачу адмяніць здзяйсненне "дадання прамежкаў у загалоўку". Вось наступныя дзеянні:

* Скапіруйце SHA дакумента, які ў дадзеным выпадку з'яўляецца `` 389004d ``
* Затым запусціце каманду ```git revert 389004d```

Гэта адкрые мой тэкставы рэдактар і прапануе мне адрэдагаваць паведамленне пра commit.
Вы можаце вырашыць пакінуць паведамленне commit як паведамленне па змаўчанні git, якое пачынаецца са слова `Revert`
альбо вы таксама можаце вырашыць наладзіць паведамленне па сваім гусце.

* Далей я буду захоўваць і закрываць тэкставы рэдактар.
* Вярнуцца да каманднага радка.
* Запусціце `` `git push origin <branch-name>` ``, каб націснуць на зваротныя змены ў Github.

І гэта ўсё, змены будуць адменены. У гэтым выпадку маё сховішча будзе зменена на тое, як яно выглядала ў `` c1b9fc1``