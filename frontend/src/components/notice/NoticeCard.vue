<template>
  <tr
    style="cursor: pointer;"
    @click="moveNoticeDetail(notice)"
  >
    <td class="text-left">{{ notice.notice_number }}</td>
    <td class="text-left">{{ notice.notice_title }}</td>
    <td>{{ notice.updated_at }}</td>
    <td>{{ notice.views }}</td>
  </tr>
</template>

<script>
import axios from 'axios';

const SERVER_URL = process.env.VUE_APP_SERVER_URL;

export default {
  name: 'NoticeCard',
  props: {
    notice: Object,
  },
  methods: {
    moveNoticeDetail(notice) {
      axios
        .get(`${SERVER_URL}/notice/views/` + notice.notice_number)
        .then(() => {
          this.$router.push({
            name: 'NoticeDetail',
            params: {
              noticenumber: notice.notice_number
            }
          })
        })
        .catch(() => {
          alert('서버와 통신할 수 없습니다.');
        });

    },
  }
}
</script>

<style>
tr > td {
  font-size: 16px !important;
}
</style>