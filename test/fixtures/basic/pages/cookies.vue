<script setup>
useCookie('accessed-but-not-used')
useCookie('accessed-with-default-value', () => 'default')
useCookie('set').value = 'set'
useCookie('set-to-null').value = null
useCookie('set-to-null-with-default', () => 'default').value = null

const updated = useCookie('updated')
// the next set are all sent by browser
useCookie('browser-accessed-but-not-used')
useCookie('browser-accessed-with-default-value', () => 'default')
useCookie('browser-set').value = 'set'
useCookie('browser-set-to-null').value = null
useCookie('browser-set-to-null-with-default', () => 'default').value = null

const objectCookie = useCookie('browser-object-default', {
  default: () => ({ foo: 'bar' })
})
</script>

<template>
  <div>
    <div>cookies testing page</div>
    <pre>{{ updated }}</pre>
    <button @click="objectCookie.foo === 'baz' ? objectCookie.foo = 'bar' : objectCookie.foo = 'baz'">
      Change cookie
    </button>
    <button @click="refreshCookie('updated')">
      Refresh cookie
    </button>
  </div>
</template>
