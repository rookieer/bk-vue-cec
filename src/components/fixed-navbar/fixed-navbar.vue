<!--
 * Tencent is pleased to support the open source community by making
 * 科技内在设计（T-inside） available.
 *
 * Copyright (C) 2021 THL A29 Limited, a Tencent company.  All rights reserved.
 *
 * 科技内在设计（T-inside） is licensed under the MIT License.
 *
 * License for 科技内在设计（T-inside）:
 *
 *
 * Terms of the MIT License:
 * ---------------------------------------------------
 * Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated
 * documentation files (the "Software"), to deal in the Software without restriction, including without limitation
 * the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and
 * to permit persons to whom the Software is furnished to do so, subject to the following conditions:
 *
 * The above copyright notice and this permission notice shall be included in all copies or substantial portions of
 * the Software.
 *
 * THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT
 * THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
 * AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF
 * CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS
 * IN THE SOFTWARE.
-->

<template>
    <div class="bk-fixed-navbar-wrapper" :class="[extCls, position]" :style="{ zIndex: localZIndex }">
        <div class="fixed-navbar-item" v-for="(item, index) in navConfig"
            :key="index"
            @click="item.action"
            v-bk-tooltips="item.tooltip">
            <i :class="['bk-icon', item.icon]"></i>
            <span class="text">{{item.text}}</span>
        </div>
    </div>
</template>

<script>
    import zIndexManager from '@/utils/z-index-manager.js'
    export default {
        name: 'bk-fixed-navbar',
        props: {
            navItems: {
                type: Array,
                default: () => []
            },
            extCls: {
                type: String,
                default: ''
            },
            position: {
                type: String,
                default: 'middle'
            }
        },
        data () {
            return {
                localZIndex: zIndexManager.nextTickIndex(2)
            }
        },
        computed: {
            navConfig () {
                const config = this.navItems.map(item => {
                    return Object.assign({
                        tooltip: { disabled: true },
                        action: () => {}
                    }, item)
                })
                return config
            }
        }
    }
</script>
<style>
@import '../../ui/fixed-navbar.css';
</style>
