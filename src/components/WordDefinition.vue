<template>
  <div v-if="definition" class="word-definition-wrapper">
    <div class="word-main">
      <div class="word-and-phonetic">
        <h1>{{definition.word}}</h1>
        <p class="phonetics">{{phonetic.text}}</p>
      </div>
      <div class="pronounce" v-if="phonetic.audio">
        <speak-word :url="phonetic.audio"/>
      </div>
    </div>
    <word-meaning
      v-for="(meaning, m) in definition.meanings"
      :meaning="meaning"
      :key="`meaning-${m}`"
    />
    <div class="horizontal-separator"></div>
    <p
      v-if="definition.sourceUrls.length"
      class="source">
      <span class="label">Source</span>
      <a
        class="link"
        :href="definition.sourceUrls[0]"
        target="_blank">{{definition.sourceUrls[0]}}<svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 14 14"><path fill="none" stroke="#838383" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M6.09 3.545H2.456A1.455 1.455 0 0 0 1 5v6.545A1.455 1.455 0 0 0 2.455 13H9a1.455 1.455 0 0 0 1.455-1.455V7.91m-5.091.727 7.272-7.272m0 0H9m3.636 0V5"/></svg>
      </a>
    </p>
  </div>
</template>

<script>
import WordMeaning from '@/components/WordMeaning.vue';
import SpeakWord from '@/components/SpeakWord.vue';

export default {
  name: 'WordDefinition',
  components: { WordMeaning, SpeakWord },
  props: {
    definition: {
      type: [Object, undefined],
    }
  },
  computed: {
    phonetic() {
      const phonetics = this.definition.phonetics ? this.definition.phonetics : [];
      const phoneticsWithAudio = phonetics.find(item => item.audio)
      return phoneticsWithAudio || { text: this.definition.phonetic, audio: '' };
    }
  },
}
</script>

<style>
.word-definition-wrapper .word-main {
  margin-bottom: 40px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.word-definition-wrapper .word-main .word-and-phonetic h1 {
  font-size: 4.48rem;
  line-height: 5.46rem;
  margin-bottom: 8px;
}

.word-definition-wrapper .word-main .word-and-phonetic p.phonetics {
  font-size: 1.58rem;
  line-height: 2.1rem;
  color: var(--purple);
}

.word-definition-wrapper .horizontal-separator {
  border-bottom: 1px solid var(--hr-color);
  margin-bottom: 20px;
}

.word-definition-wrapper p.source {
  text-decoration: underline;
}

.word-definition-wrapper p.source span {
  display: inline-block;
  text-decoration: underline;
}

.word-definition-wrapper p.source span.label {
  color: var(--grey-variant-1);
  margin-right: 20px;
}

.word-definition-wrapper p.source a.link {
  color: var(--text-color);
}

.word-definition-wrapper p.source a.link svg {
  vertical-align: middle;
  margin-left: 10px;
}
</style>
