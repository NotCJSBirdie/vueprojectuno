<template>
  <div>
    <Menu>
      <MenuButton>More</MenuButton>
      <MenuItems class="flex flex-col items-center bg-white text-black p-6">
        <MenuItem v-slot="{ active }">
          <a :class='{ "bg-blue-500": active }' href="/account-settings">
            Account settings
          </a>
        </MenuItem>
        <MenuItem v-slot="{ active }">
          <a :class='{ "bg-blue-500": active }' href="/account-settings">
            Documentation
          </a>
        </MenuItem>
        <MenuItem disabled>
          <span class="opacity-75">Invite a friend (coming soon!)</span>
        </MenuItem>
      </MenuItems>
    </Menu>


    <div>
      <!-- The button to open modal -->
<label for="my-modal" class="btn modal-button">open modal</label>

<!-- Put this part before </body> tag -->
<input type="checkbox" id="my-modal" class="modal-toggle">
<div class="modal">
  <div class="modal-box">
    <h3 class="font-bold text-lg">Congratulations random Interner user!</h3>
    <p class="py-4">You've been selected for a chance to get one year of subscription to use Wikipedia for free!</p>
    <div class="modal-action">
      <label for="my-modal" class="btn">Yay!</label>
    </div>
  </div>
</div>
    </div>

    <div class="overflow-x-auto">
  <table class="table table-zebra w-full" >
    <!-- head -->
    <thead>
      <tr>
     
        <th @click="sortName">Name</th>
        <th>Role</th>
        <th>Client</th>
        <th>Status</th>
        <th>Last Update</th>
        <th>Action</th>
      </tr>
    </thead>
    <tbody >
      <!-- row 1 -->
      <tr v-for="persons in count">
     
        <td>{{persons.name}}</td>
        <td>{{persons.role.name}}</td>
        <td>{{persons.client.name}}</td>
        <td>
          <div v-if="persons.status == 'T'">
  Technical Interview
</div>
<div v-else-if="persons.status === 'C'">
 Client Interview
</div>
<div v-else-if="persons.status === 'I'">
  Initial Interview
</div>
<div v-else>
  Waiting
</div>
        </td>
        <td>{{persons.updatedAt}}</td>
        <td>
          <div class="dropdown dropdown-end">
  <label tabindex="0" class=" m-1">
     <svg xmlns="http://www.w3.org/2000/svg" class="icon icon-tabler icon-tabler-dots" width="20" height="20" viewBox="0 0 24 24" stroke-width="1.5" stroke="#2c3e50" fill="none" stroke-linecap="round" stroke-linejoin="round">
                  <path stroke="none" d="M0 0h24v24H0z" fill="none"/>
                  <circle cx="5" cy="12" r="1" />
                  <circle cx="12" cy="12" r="1" />
                  <circle cx="19" cy="12" r="1" />
                </svg>
  </label>
  <ul tabindex="0" class="dropdown-content menu p-2 shadow bg-base-100 rounded-box w-52">
    <li><a>Item 1</a></li>
    <li><a>Item 2</a></li>
  </ul>
</div>
          
        </td>
      </tr>
     
    </tbody>
  </table>
</div>
  </div>
</template>

<style>

</style>

<script setup lang="ts">
import { Menu, MenuButton, MenuItems, MenuItem } from '@headlessui/vue';
import { reactive } from 'vue';
import { computed } from 'vue';
import {
    Listbox,
    ListboxButton,
    ListboxOptions,
    ListboxOption,
  } from '@headlessui/vue'

const status = []

const count = reactive([
  {
    name: "Margaret Mclaughlin",
    role: {
      name: "Dev Ops Engineer",
    },
    client: {
      name: "Cosmogence"
    },
    status: "T",
    updatedAt: 
      "Just Now",
  },
  {
    name: "Harold Spencer",
    role: {
      name: "Flutter Developer",
    },
    client: {
      name: "iClickSee",
    },
    status: 
      "T",
    updatedAt: "5 mins ago",   
  },
  {
    name: "Virgil Walters",
    role: {
      name: "Junior Developer",
    },
    client: {
      name: "EonX",
    },
    status: "T",
    updatedAt: "5 mins ago",
  },
  {
    name: "Julian Zimmerman",
    role: {
      name: "Senior Software Engineer",
    },
    client: {
      name: "EonX",
    },
    status: "T",
    updatedAt: "5 mins ago",
  },
  {
    name: "Barry Payne",
    role: {
      name: "Back end Developer",
    },
    client: {
      name: "Flexisource IT",
    },
    status: "C",
    updatedAt: "6 mins ago",
  },
  {
    name: "Annie Rose",
    role: {
      name: "Lead Developer",
    },
    client: {
      name: "Filta",
    },
    status: "C",
    updatedAt: "6 mins ago",
  },
  {
    name: "Jacqueline May",
    role: {
      name: "Full Stack Developer",
    },
    client: {
      name: "Flexisource IT",
    },
    status: "C",
    updatedAt: "8 mins ago",
  },
  {
    name: "Bobbie Hudson",
    role: {
      name: "Front end Developer",
    },
    client: {
      name: "Accenture",
    },
    status: "I",
    updatedAt: "9 mins ago",
  },
  {
    name: "Darren Long",
    role: {
      name: "Senior PHP Developer",
    },
    client: {
      name: "Zap Group",
    },
    status: "I",
    updatedAt: "30 mins ago",
  },
  {
    name: "Ruth Jenkins",
    role: {
      name: "Senior Developer",
    },
    client: {
      name: "iClickSee",
    },
    status: "I",
    updatedAt: "1 hour ago",
  },
  {
    name: "Stephanie Wright",
    role: {
      name: "Wordpress & Web Developer",
    },
    client: {
      name: "iClickSee",
    },
    status: "I",
    updatedAt: "1 day ago",
  },
  {
    name: "Javier Carroll",
    role: {
      name: "QA Engineer",
    },
    client: {
      name: "Flexisource IT",
    },
    status: "W",
    updatedAt: "04/03/2022",
  },
])

const sortName = computed(
  function sortName() {
    count.sort((a,b)=>{
      let fa = a.name.toLowerCase(), fb = b.name.toLowerCase();
			if (fa < fb) {
				return -1
			}
			if (fa > fb) {
				return 1
			}
			return 0
    })
  }
)

const sortRole = computed(
  function sortRole() {
    count.sort((a,b)=>{
      let fa = a.role.name.toLowerCase(), fb = b.role.name.toLowerCase();
			if (fa < fb) {
				return -1
			}
			if (fa > fb) {
				return 1
			}
			return 0
    })
  }
)

const sortClient = computed(
  function sortClient() {
    count.sort((a,b)=>{
      let fa = a.client.name.toLowerCase(), fb = b.client.name.toLowerCase();
			if (fa < fb) {
				return -1
			}
			if (fa > fb) {
				return 1
			}
			return 0
    })
  }
)

const sortStatus = computed(
  function sortStatus() {
    count.sort((a,b)=>{
      let fa = a.status.toLowerCase(), fb = b.status.toLowerCase();
			if (fa < fb) {
				return -1
			}
			if (fa > fb) {
				return 1
			}
			return 0
    })
  }
)

const sortUpdated = computed(
  function sortUpdated() {
    count.sort((a,b)=>{
      let fa = a.updatedAt.toLowerCase(), fb = b.updatedAt.toLowerCase();
			if (fa < fb) {
				return -1
			}
			if (fa > fb) {
				return 1
			}
			return 0
    })
  }
)

</script>
