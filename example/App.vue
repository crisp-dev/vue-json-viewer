<template>
  <div>
    <json-viewer
      preview-mode
      :value="{'data': {'data': {'data': {'a': 1}}}}"
    ></json-viewer>
    <json-viewer :value="jsonData"></json-viewer>
    <hr />
    <json-viewer
      :value="jsonData"
      :expand-depth="5"
      :copyable="{ copyText: '复制', copiedText: '复制成功', align: 'left' }"
      boxed
      :timeformat="(time) => new Date(time)"
      sort
      ></json-viewer>
    <hr />
    <json-viewer
      :value="jsonData"
      :expand-depth="1"
      :copyable="{ timeout: 4000, align: 'left' }"
      :onCopied="onCopied"
    >
      <template v-slot:copy="{ copied }">
        <button v-if="copied" disabled>Copied!</button>
        <button v-else>Copy me!</button>
      </template>
    </json-viewer>
  </div>
</template>

<script>
export default {
  data() {
    return {
      jsonData: {
        total: 25,
        limit: 10,
        skip: 0,
        numbers: 10.11,
        success: true,
        links: {
          previous: undefined,
          next: function () {},
        },
        data: [
          {
            id: '5968fcad629fa84ab65a5247',
            firstname: 'Ada',
            link: 'http://google.com',
            lastname: 'Lovelace',
            awards: null,
            known: [
              'mathematics',
              'computing'
            ],
            position: {
              lat: 44.563836,
              lng: 6.495139
            },
            description: `Augusta Ada King, Countess of Lovelace (née Byron; 10 December 1815 – 27 November 1852) was an English mathematician and writer,
            chiefly known for her work on Charles Babbage's proposed mechanical general-purpose computer,
            the Analytical Engine. She was the first to recognise that the machine had applications beyond pure calculation,
            and published the first algorithm intended to be carried out by such a machine.
            As a result, she is sometimes regarded as the first to recognise the full potential of a "computing machine" and the first computer programmer.`,
            bornAt: new Date('1815-12-10T00:00:00.000Z'),
            diedAt: new Date('1852-11-27T00:00:00.000Z')
          }, {
            id: '5968fcad629fa84ab65a5246',
            firstname: 'Grace',
            lastname: 'Hopper',
            awards: [
              'Defense Distinguished Service Medal',
              'Legion of Merit',
              'Meritorious Service Medal',
              'American Campaign Medal',
              'World War II Victory Medal',
              'National Defense Service Medal',
              'Armed Forces Reserve Medal',
              'Naval Reserve Medal',
              'Presidential Medal of Freedom'
            ],
            known: null,
            position: {
              lat: 43.614624,
              lng: 3.879995
            },
            description: `Grace Brewster Murray Hopper (née Murray; December 9, 1906 – January 1, 1992)
            was an American computer scientist and United States Navy rear admiral.
            One of the first programmers of the Harvard Mark I computer,
            she was a pioneer of computer programming who invented one of the first compiler related tools.
            She popularized the idea of machine-independent programming languages, which led to the development of COBOL,
            an early high-level programming language still in use today.`,
            bornAt: new Date('1815-12-10T00:00:00.000Z'),
            diedAt: new Date('1852-11-27T00:00:00.000Z')
          }
        ]
      }
    }
  },
  methods: {
    onCopied(copyEvent) {
      alert(`Text successfully copied!\n${copyEvent.text}`);
    }
  }
};
</script>

<style lang="scss">
.jv-number-float {
  color: #faa !important;
}
.jv-key-node {
  display: flex;
}
</style>