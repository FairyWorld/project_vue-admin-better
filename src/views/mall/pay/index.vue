<template>
  <div class="pay-container">
    <vab-page-header description="安全便捷的支付流程，支持多种支付方式" :icon="['fas', 'credit-card']" title="支付中心" />

    <el-row :gutter="20">
      <el-col
        :lg="{ span: 14, offset: 5 }"
        :md="{ span: 20, offset: 2 }"
        :sm="{ span: 20, offset: 2 }"
        :xl="{ span: 12, offset: 6 }"
        :xs="24"
      >
        <el-steps :active="active" align-center class="steps" :space="200">
          <el-step title="填写转账信息" />
          <el-step title="确认转账信息" />
          <el-step title="完成" />
        </el-steps>
        <step1 v-if="active === 1" @change-step="handleSetStep" />
        <step2 v-if="active === 2" :info-data="form" @change-step="handleSetStep" />
        <step3 v-if="active === 3" :info-data="form" @change-step="handleSetStep" />
      </el-col>
    </el-row>
  </div>
</template>

<script>
  import Step1 from './components/Step1'
  import Step2 from './components/Step2'
  import Step3 from './components/Step3'
  import VabPageHeader from '@/components/VabPageHeader'

  export default {
    name: 'Pay',
    components: {
      Step1,
      Step2,
      Step3,
      VabPageHeader,
    },
    data() {
      return {
        active: 1,
        form: {},
      }
    },
    methods: {
      handleSetStep(active, form) {
        this.active = active
        if (form) this.form = Object.assign(this.form, form)
      },
    },
  }
</script>
<style lang="scss" scoped>
  .pay-container {
    .steps {
      justify-content: center;
      margin-bottom: 20px;
    }
  }
</style>
