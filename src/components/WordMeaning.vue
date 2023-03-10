<template>
  <div v-if="meaning" class="word-meaning">
    <div class="part-of-speech">
      <h3>{{meaning.partOfSpeech}}</h3>
      <span class="border"></span>
    </div>
    <h5>Meaning</h5>
    <ul class="meaning-list">
      <li
        v-for="(item, i) in meaning.definitions"
        :key="`definition-${i}`"
      >
        {{ item.definition }}
        <span v-if="item.example" class="example">
          "{{ item.example }}"
        </span>
      </li>
    </ul>
    <h5 v-if="meaning.synonyms.length">
      Synonyms <span>{{meaning.synonyms.join(', ')}}</span>
    </h5>
  </div>
</template>

<script>
export default {
  name: 'WordMeaning',
  props: {
    meaning: {
      type: Object,
    }
  }
}
</script>

<style>
.word-meaning {
  margin-bottom: 40px;
}

.word-meaning .part-of-speech {
  display: flex;
  margin-bottom: 40px;
}

.word-meaning .part-of-speech h3 {
  font-size: 1.68rem;
  line-height: 2.1rem;
  font-weight: 700;
  font-style: italic;
}

.word-meaning .part-of-speech span {
  display: inline-block;
  flex-grow: 1;
  position: relative;
}

.word-meaning .part-of-speech span:after {
  content: '';
  position: absolute;
  height: 1px;
  width: calc(100% - 20px);
  top: 50%;
  right: 0;
  background-color: var(--hr-color);
  transition: 0.3s ease-in-out;
}

.word-meaning h5 {
  font-size: 1.4rem;
  line-height: 1.68rem;
  color: var(--grey-variant-1);
  font-weight: 400;
  margin-bottom: 24px;
}

.word-meaning h5 span {
  color: var(--purple);
  font-weight: 700;
  margin-left: 20px;
}

.word-meaning ul.meaning-list {
  margin-left: 22px;
  margin-bottom: 40px;
  list-style: none;
}

.word-meaning ul.meaning-list li {
  font-size: 1.26rem;
  line-height: 1.68rem;
  margin-bottom: 12px;
  padding-left: 25px;
  position: relative;
}

.word-meaning ul.meaning-list li:before {
  content: '';
  display: inline-block;
  width: 5px;
  height: 5px;
  border-radius: 5px;
  background-color: var(--purple);
  position: absolute;
  left: 0;
  top: 10px;
}

.word-meaning ul.meaning-list li span.example {
  display: block;
  color: var(--grey-variant-1);
  margin-top: 12px;
}
</style>
