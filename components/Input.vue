<select name="select" @click="select = $event.target.value">
        <option value="">filter</option>
        <option v-for="user of list" :key="user.id" :value="user.company.bs">
          {{ user.company.bs }}
        </option>
      </select>
