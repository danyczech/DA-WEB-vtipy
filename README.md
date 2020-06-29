# Dad Jokes

Tvým úkolem je vytvořit aplikaci, která bude zobrazovat seznam vtipů. U každého vtipu půjde kliknutím na tlačítko zvětšovat počet lajků a nelajků (palec nahoru / palec dolů).

V kořenové složce projektu je video **ukazka-fungovani.mp4**, kde se můžeš podívat, jak má celá jednoduchá aplikace vypadat.

V kořenové složce projektu je také soubor jokes.txt. Ten obsahuje seznam vtipů, včetně jména uživatele a počtu lajků a nelajků.

**Nezapomeň na konci práce udělat *commit* všech změn a hlavně *push* do repozitáře na GitHubu.**


## Zadání a postup

1. **V App.vue vytvořte v datech seznam vtipů** - pole objektů, kde každý objekt představuje jeden vtip. Každý vtip musí mít následující vlastnosti:

	 - text vtipu
   - název uživatele - slouží jako název ikonky, která se má u vtipu zobrazit
   - počet lajků (palců nahoru, kolikrát se vtip líbil)
   - počet nelajků (palců dolů, kolikrát se vtip nelíbil)

   Seznam vtipů najdete v kořenové složce projektu v souboru vtipy.txt nebo na adrese xxxxx.yyy.

2. **Vytvořte komponentu Joke**, která bude zobrazovat jeden vtip. Údaje, které se mají v komponentě zobrazit, předejte do komponenty jako props.

   V komentáři uvnitř App.vue najdete zakomentovaný kód pro HTML strukturu jednoho vtipu. Z toho HTML vytvořte šablonu komponenty Joke.

	 Pro jistotu šablonu uvádíme i zde:

	 ```
	<div class="joke">
      <div class="joke-body">
        <img class="joke-user" src="/images/users/user01.png" />
        <p class="joke-text">
          The secret service isn't allowed to yell "Get down!" anymore when the president is about to be attacked. Now they have to yell "Donald, duck!"
        </p>
      </div>
      <div class="joke-likes">
        <button class="btn-like btn-up"></button>
        <span class="likes-count likes-up">0</span>

        <button class="btn-like btn-down"></button>
        <span class="likes-count likes-down">0</span>
      </div>
    </div>
	 ```

3. **V HTML šabloně uvnitř App.vue zobrazte pod sebou všechny vtipy** - tj. pomocí v-for opakujte komponentu Joke pro každý vtip z pole vtipů, které jste vytvořili v datech v prvním kroku.

   Uvnitř komponenty Joke zařiďte, aby se klikáním na palec nahoru nebo dolů zvětšoval počet příslušných lajků/nelajků.

   Komponenta by neměla měnit svoje vlastní data (získaná z props), ale požadavek na změnu počtu lajků (palec nahoru) nebo nelajků (palec dolů) emitovat do mateřské komponenty App.vue, kde teprve ke změně počtu u příslušného vtipu dojde.

4. **Uvnitř komponenty nezapomeň:**

   - komponenta přijímá všechny potřebné props
	 - nyní jsou v šabloně vzorová data natvrdo - místo nich zobrazuj na příslušných místech údaje získané z prosps
	 - změnu lajků/nelajků potřebujeme emitovat jako událost do rodičovské Vue.app
	 - v rodičovské Vue.app na emitované události reagujeme a teprve tam měníme příslušná data u správného vtipu

Hodně štěstí.