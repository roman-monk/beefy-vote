<template>
  <UiModal :open="open" @close="$emit('close')">
    <h3 class="m-4 text-center">About</h3>
    <div class="text-center">
      <a href="https://twitter.com/beefyfinance" target="_blank">
        <Icon size="32" name="twitter" class="mr-1 mx-2" />
      </a>
      <a href="https://discord.gg/yq8wfHd" target="_blank">
        <Icon size="32" name="discord" class="mr-1 mx-2" />
      </a>
      <a href="https://t.me/beefyfinance" target="_blank">
        <Icon size="32" name="telegram" class="mr-1 mx-2" />
      </a>
      <a :href="`https://github.com/beefyfinance/beefy-vote`" target="_blank">
        <Icon size="32" name="github" class="mr-1 mx-2" />
      </a>
    </div>
    <div class="m-4 p-4 border rounded-2 text-white">
      <div class="d-flex">
        <span v-text="'Version'" class="flex-auto text-gray mr-1" />
        {{ pkg.version }}
      </div>
      <div class="d-flex">
        <span v-text="'License'" class="flex-auto text-gray mr-1" />
        {{ pkg.license }}
      </div>
      <div class="d-flex">
        <span v-text="'Network'" class="flex-auto text-gray mr-1" />
        Binance Smart Chain
      </div>
      <div class="d-flex">
        <span v-text="'Block number'" class="flex-auto text-gray mr-1" />
        <a
          :href="_bscscanLink(web3.blockNumber, 'block')"
          target="_blank"
          class="float-right"
        >
          {{ $n(web3.blockNumber) }}
          <Icon name="external-link" class="ml-1" />
        </a>
      </div>
      <div class="d-flex">
        <span v-text="'IPFS server'" class="flex-auto text-gray mr-1" />
        {{ ipfsNode }}
      </div>
      <div class="d-flex">
        <span v-text="'Hub'" class="flex-auto text-gray mr-1" />
        {{ hubUrl }}
      </div>
    </div>
  </UiModal>
</template>

<script>
import pkg from '@/../package.json';

export default {
  props: ['open'],
  data() {
    return {
      pkg,
      hubUrl: 'https://beefy-vote-api.herokuapp.com',
      ipfsNode: 'ipfs.io',
    };
  },
};
</script>
