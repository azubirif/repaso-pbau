<script>
  import "./output.css";
  import { onMount } from "svelte";
  
  let cat = false, cast = false, filo = false, he = false;

  onMount(() => {
    let pre_cat = localStorage.getItem("cat");
    if (pre_cat != null) { cat = !JSON.parse(pre_cat); }

    let pre_cast = localStorage.getItem("cast");
    if (pre_cast != null) { cast = !JSON.parse(pre_cast); }

    let pre_filo = localStorage.getItem("filo");
    if (pre_filo != null) { filo = !JSON.parse(pre_filo); }

    let pre_he = localStorage.getItem("he");
    if (pre_he != null) { he = !JSON.parse(pre_he); }
  });

  let texto = ":(";

  const contenido = {
    "cat": ["1. Definició", "2. Llengües en el món", "3. Contacte entre llengües", "4. Mitifcació del bilingüisme", "5. Bilingüe i bilingüista", "6. Processos de substitució", "7. Processos de normalització y planificació lingüístca", "8. Models de planificació lingüístca", "9. Prejudicis lingüístics", "10. Realidad plurilingüe", "11. Marc legal", "12. Realitat sociolingüística", "Variació lingüística", "Registres lingüístics", "Tipus de registre", "L'estàndard"],
    "cast": ["Modernismo", "Generación del 98", "Generación del 27", "Vanguardias", "Teatro de preguerra"],
    "filo": ["Platón - Alma", "Platón - Conocimiento","Platón - Política", "Platón - Ideas", "Platón - Caverna", "Aristóteles - Ética", "Aristóteles - Sustancia", "Aristóteles - Hilemorfismo", "Aristóteles - Política", "Aristóteles - Conocimiento", "Aristóteles - Alma", "Aristóteles - Virtud", "Descartes - Metodo", "Descartes - Sustancia", "Descartes - Tipos de ideas", "Descartes - Existencia de Dios", "Descartes - Conocimiento", "Hume - Ideas", "Hume - Ética", "Hume - Crítica metafísica", "Hume - Crítica causalidad"],
    "he": ["Franquismo - Características", "Franquismo - 2da Guerra Mundial", "Franquismo - Desarrollismo", "Franquismo - Crisis", "Alfonso XIII 1ra","Alfonso XIII 2da", "Crisis Restauración Borbónica", "Sexenio Democrático 2", "Final Primo de Rivera", "Guerra del Francés", "Reinado Carlos IV", "Guerra Civil", "Bienio Reformista", "Bienio Conservador", "Gobierno Frente Popular", "Directorio Civil", "Reinado Isabel II", "Directorio Militar", "Sexenio Democrático 1", "Reinado Fernando VII", "Etapas Isabel II"],
  };

  function updateCat() {
    localStorage.setItem("cat", JSON.stringify(cat));
  }

  function updateCast() {
    localStorage.setItem("cast", JSON.stringify(cast));
  }

  function updateFilo() {
    localStorage.setItem("filo", JSON.stringify(filo));
  }

  function updateHe() {
    localStorage.setItem("he", JSON.stringify(he));
  }

  function updateText()
  {
    let temas = [];
    if (cat) { temas.push("cat") };
    if (cast) { temas.push("cast") };
    if (filo) { temas.push("filo") };
    if (he) { temas.push("he") };

    if (temas.length == 0) texto = ":(";
    else {
      let tema = temas[Math.floor(Math.random() * temas.length)];
      let apartado = contenido[tema][Math.floor(Math.random() * contenido[tema].length)];

      texto = apartado;
    }
  }
</script>

<main class="w-screen h-screen bg-green-500 flex justify-center items-center">
  <div class="absolute top-3 flex flex-col gap-3">
    <div class="flex flex-row gap-2">
      <input on:change={updateCat} bind:checked={cat} type="checkbox" name="" id="cat">
      <label class="text-xl text-white font-bold" for="cat">Catalán - Sociolingüístca</label>
    </div>
    <div class="flex flex-row gap-2">
      <input on:change={updateCast} bind:checked={cast}  type="checkbox" name="" id="cast">
      <label class="text-xl text-white font-bold" for="cast">Castellano - Preguerra</label>
    </div>
    <div class="flex flex-row gap-2">
      <input on:change={updateFilo} bind:checked={filo} type="checkbox" name="" id="filo">
      <label class="text-xl text-white font-bold" for="filo">Filosofía - 4 primeros autores</label>
    </div>
    <div class="flex flex-row gap-2">
      <input on:change={updateHe} bind:checked={he} type="checkbox" name="" id="he">
      <label class="text-xl text-white font-bold" for="he">Historia - Todo :)</label>
    </div>
  </div>

  <div class="flex flex-col items-center justify-center gap-6">
    <h1 class="text-5xl text-white">{texto}</h1>
    <button class="px-2 py-1 bg-white rounded-xl font-bold" on:click={updateText}>Cambiar</button>
  </div>
</main>