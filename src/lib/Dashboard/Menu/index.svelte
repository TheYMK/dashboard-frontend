<script>
  	import userStore from '../../../stores/user'
    import navigationStore from '../../../stores/navigation'


    const switchMenu = (path) => {
      navigationStore.set({active: path})
    }

</script>
<ul class="menu bg-primary text-white w-56 h-screen">
  {#if $userStore && $userStore.role === 'user'}
    <li on:click={() => switchMenu("allDevices")} class={$navigationStore && $navigationStore.active === 'allDevices' ? 'bg-blue-400' : ''}><a><i class="fa-solid fa-server"></i> My Devices</a></li>
    <li on:click={() => switchMenu("map")} class={$navigationStore && $navigationStore.active === 'map' ? 'bg-blue-400' : ''}><a><i class="fa-solid fa-server"></i> View Map</a></li>
  {:else if $userStore && $userStore.role === 'admin'}
    <li on:click={() => switchMenu("allUsers")} class={$navigationStore && $navigationStore.active === 'allUsers' ? 'bg-blue-400' : ''}><a><i class="fa-solid fa-users"></i> Manage Users</a></li>
  {:else if $userStore && $userStore.role === 'superadmin'}
    <li on:click={() => switchMenu("allAdmins")} class={$navigationStore && $navigationStore.active === 'allAdmins' ? 'bg-blue-400' : ''}><a><i class="fa-solid fa-users"></i> Manage Admins</a></li>
  {/if}
</ul>
<style>
  /* your styles go here */
</style>