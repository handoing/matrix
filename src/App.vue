<template>
    <div>
        <vue-mathjax :formula="'$$x = {-b \\pm \\sqrt{b^2-4ac} \\over 2a}.$$'"></vue-mathjax>
    </div>
    <div class="grid">
        <div class="cell" v-for="_ in cells"><span></span></div>
    </div>

    <div class="mask"
        :style="{ transform: `matrix3d(${a1}, ${b1}, ${c1}, ${d1}, ${a2}, ${b2}, ${c2}, ${d2}, ${a3}, ${b3}, ${c3}, ${d3}, ${a4}, ${b4}, ${c4}, ${d4})` }">
        <div class="grid">
            <div class="cell" v-for="_ in cells"><span></span></div>
        </div>
        <div class="grid" style="transform: rotateY(90deg);left: 100%;transform-origin: 0 0;">
            <div class="cell" v-for="_ in cells"><span></span></div>
        </div>
        <div class="base"></div>
        <div class="box source"></div>
        <div class="box target" :style="{ transform: `matrix(${a}, ${b}, ${c}, ${d}, ${tx}, ${ty})` }">target</div>
    </div>

    <div class="control">
        <span>a: {{ a }}</span>
        <input v-model="a" type="range" min="0" max="10" step="0.1" />
    </div>
    <div class="control">
        <span>b: {{ b }}</span>
        <input v-model="b" type="range" min="0" max="10" step="0.1" />
    </div>
    <div class="control">
        <span>c: {{ c }}</span>
        <input v-model="c" type="range" min="0" max="10" step="0.1" />
    </div>
    <div class="control">
        <span>d: {{ d }}</span>
        <input v-model="d" type="range" min="0" max="10" step="0.1" />
    </div>
    <div class="control">
        <span>tx: {{ tx }}</span>
        <input v-model="tx" type="range" min="-250" max="250" />
    </div>
    <div class="control">
        <span>ty: {{ tx }}</span>
        <input v-model="ty" type="range" min="-250" max="250" />
    </div>

    <div class="control">
        <span>a1: {{ a1 }}</span>
        <input v-model="a1" type="range" min="0" max="10" step="0.1" />
    </div>
    <div class="control">
        <span>b1: {{ b1 }}</span>
        <input v-model="b1" type="range" min="0" max="10" step="0.1" />
    </div>
    <div class="control">
        <span>c1: {{ c1 }}</span>
        <input v-model="c1" type="range" min="0" max="10" step="0.1" />
    </div>
    <div class="control">
        <span>d1: {{ d1 }}</span>
        <input v-model="d1" type="range" min="0" max="10" step="0.1" />
    </div>
    <div class="control">
        <span>a2: {{ a2 }}</span>
        <input v-model="a2" type="range" min="0" max="10" step="0.1" />
    </div>
    <div class="control">
        <span>b2: {{ b2 }}</span>
        <input v-model="b2" type="range" min="0" max="10" step="0.1" />
    </div>
    <div class="control">
        <span>c2: {{ c2 }}</span>
        <input v-model="c2" type="range" min="0" max="10" step="0.1" />
    </div>
    <div class="control">
        <span>d2: {{ d2 }}</span>
        <input v-model="d2" type="range" min="0" max="10" step="0.1" />
    </div>
    <div class="control">
        <span>a3: {{ a3 }}</span>
        <input v-model="a3" type="range" min="0" max="10" step="0.1" />
    </div>
    <div class="control">
        <span>b3: {{ b3 }}</span>
        <input v-model="b3" type="range" min="0" max="10" step="0.1" />
    </div>
    <div class="control">
        <span>c3: {{ c3 }}</span>
        <input v-model="c3" type="range" min="0" max="10" step="0.1" />
    </div>
    <div class="control">
        <span>d3: {{ d3 }}</span>
        <input v-model="d3" type="range" min="0" max="10" step="0.1" />
    </div>
    <div class="control">
        <span>a4: {{ a4 }}</span>
        <input v-model="a4" type="range" min="0" max="10" step="0.1" />
    </div>
    <div class="control">
        <span>b4: {{ b4 }}</span>
        <input v-model="b4" type="range" min="0" max="10" step="0.1" />
    </div>
    <div class="control">
        <span>c4: {{ c4 }}</span>
        <input v-model="c4" type="range" min="0" max="10" step="0.1" />
    </div>
    <div class="control">
        <span>d4: {{ d4 }}</span>
        <input v-model="d4" type="range" min="0" max="10" step="0.1" />
    </div>
    <button @click="reset">reset</button>

    <br/>
    <math>
        <mrow>
            <mi>A</mi>
            <mo>=</mo>
            <mfenced open="[" close="]">
                <mtable>
                    <mtr>
                        <mtd>
                            <mi>{{ a }}</mi>
                        </mtd>
                        <mtd>
                            <mi>{{ c }}</mi>
                        </mtd>
                        <mtd>
                            <mi>{{ tx }}</mi>
                        </mtd>
                    </mtr>
                    <mtr>
                        <mtd>
                            <mi>{{ b }}</mi>
                        </mtd>
                        <mtd>
                            <mi>{{ d }}</mi>
                        </mtd>
                        <mtd>
                            <mi>{{ ty }}</mi>
                        </mtd>
                    </mtr>
                    <mtr>
                        <mtd>
                            <mi>0</mi>
                        </mtd>
                        <mtd>
                            <mi>0</mi>
                        </mtd>
                        <mtd>
                            <mi>1</mi>
                        </mtd>
                    </mtr>
                </mtable>
            </mfenced>
        </mrow>
    </math>

    <br/>
    <math>
        <mrow>
            <mi>B</mi>
            <mo>=</mo>
            <mfenced open="[" close="]">
                <mtable>
                    <mtr>
                        <mtd>
                            <mi>{{ a1 }}</mi>
                        </mtd>
                        <mtd>
                            <mi>{{ a2 }}</mi>
                        </mtd>
                        <mtd>
                            <mi>{{ a3 }}</mi>
                        </mtd>
                        <mtd>
                            <mi>{{ a4 }}</mi>
                        </mtd>
                    </mtr>
                    <mtr>
                        <mtd>
                            <mi>{{ b1 }}</mi>
                        </mtd>
                        <mtd>
                            <mi>{{ b2 }}</mi>
                        </mtd>
                        <mtd>
                            <mi>{{ b3 }}</mi>
                        </mtd>
                        <mtd>
                            <mi>{{ b4 }}</mi>
                        </mtd>
                    </mtr>
                    <mtr>
                        <mtd>
                            <mi>{{ c1 }}</mi>
                        </mtd>
                        <mtd>
                            <mi>{{ c2 }}</mi>
                        </mtd>
                        <mtd>
                            <mi>{{ c3 }}</mi>
                        </mtd>
                        <mtd>
                            <mi>{{ c4 }}</mi>
                        </mtd>
                    </mtr>
                    <mtr>
                        <mtd>
                            <mi>{{ d1 }}</mi>
                        </mtd>
                        <mtd>
                            <mi>{{ d2 }}</mi>
                        </mtd>
                        <mtd>
                            <mi>{{ d3 }}</mi>
                        </mtd>
                        <mtd>
                            <mi>{{ d4 }}</mi>
                        </mtd>
                    </mtr>
                </mtable>
            </mfenced>
        </mrow>
    </math>


    <div>({{a}}, {{b}}, {{c}}, {{d}}, {{tx}}, {{ty}})</div>
    <div>({{a1}}, {{b1}}, {{c1}}, {{d1}}, {{a2}}, {{b2}}, {{c2}}, {{d2}}, {{a3}}, {{b3}}, {{c3}}, {{d3}}, {{a4}}, {{b4}}, {{c4}}, {{d4}})</div>

</template>

<script setup>
import { ref } from "vue";

const cells = 10 * 10;
// const formula = ref('$$x = {-b \\pm \\sqrt{b^2-4ac} \\over 2a}.$$');

const a = ref(1);
const b = ref(0);
const c = ref(0);
const d = ref(1);
const tx = ref(0);
const ty = ref(0);

// const a1 = ref(1);
const a1 = ref(calculateCosAndSin(80).cos);
const b1 = ref(0);
// const c1 = ref(0);
const c1 = ref(-calculateCosAndSin(80).sin);
const d1 = ref(0);
const a2 = ref(0);
const b2 = ref(1);
const c2 = ref(0);
const d2 = ref(0);
// const a3 = ref(0);
const a3 = ref(calculateCosAndSin(80).sin);
const b3 = ref(0);
// const c3 = ref(1);
const c3 = ref(calculateCosAndSin(80).cos);
const d3 = ref(0);
const a4 = ref(0);
const b4 = ref(0);
const c4 = ref(0);
const d4 = ref(1);

function calculateCosAndSin(degrees) {
    const radians = degrees * (Math.PI / 180); // 转换为弧度
    const cosValue = Math.cos(radians); // 计算余弦
    const sinValue = Math.sin(radians); // 计算正弦
    return { cos: cosValue, sin: sinValue };
}

const reset = () => {
    a.value = 1;
    b.value = 0;
    c.value = 0;
    d.value = 1;
    tx.value = 0;
    ty.value = 0;

    a1.value = 1;
    b1.value = 0;
    c1.value = 0;
    d1.value = 0;
    a2.value = 0;
    b2.value = 1;
    c2.value = 0;
    d2.value = 0;
    a3.value = 0;
    b3.value = 0;
    c3.value = 1;
    d3.value = 0;
    a4.value = 0;
    b4.value = 0;
    c4.value = 0;
    d4.value = 1;
}

</script>

<style>
:root {
    --container-width: 500px;
    --line-width: 2px;
    --border-width: calc(var(--line-width) / 2);
}

.grid {
    display: grid;
    grid-template-columns: repeat(10, 1fr);
    grid-template-rows: repeat(10, 1fr);
    width: var(--container-width);
    height: var(--container-width);
    border: 1px solid #333;
    position: absolute;
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
    margin: auto;
    z-index: -2;
}

.cell {
    border-color: #ccc;
    border-style: dashed;
    border-width: var(--border-width);
    display: flex;
    justify-content: center;
    align-items: center;
}

.mask {
    width: var(--container-width);
    height: var(--container-width);
    border: 1px solid #333;
    position: absolute;
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
    margin: auto;
    z-index: -1;
}

.mask .base {
    width: calc(var(--line-width) * 2);
    height: calc(var(--line-width) * 2);
    background-color: red;
    position: absolute;
    left: calc(var(--container-width) / 2 - var(--line-width));
    top: calc(var(--container-width) / 2 - var(--line-width));
}

.mask .box {
    width: calc(var(--container-width) / 10);
    height: calc(var(--container-width) / 10);
    background-color: rgba(0, 255, 0, .5);
    position: absolute;
    left: calc(var(--container-width) / 2);
    top: calc(var(--container-width) / 2);
    transform-origin: 0 0;
}

.mask .box.target {
    background-color: rgba(255, 0, 0, .5);
}

.control {
    width: 240px;
    display: grid;
    grid-template-columns: 1fr 2fr;
}

input {
    cursor: grab;
}

input:active {
    cursor: grabbing;
}
</style>