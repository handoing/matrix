<template>
    <div class="grid">
        <div class="cell" v-for="_ in cells"><span></span></div>
    </div>

    <div class="mask"
        :style="{ transform: `matrix3d(${a1}, ${b1}, ${c1}, ${d1}, ${a2}, ${b2}, ${c2}, ${d2}, ${a3}, ${b3}, ${c3}, ${d3}, ${a4}, ${b4}, ${c4}, ${d4})` }">
        <div class="grid" style="">
            <div class="cell" v-for="_ in cells"><span></span></div>
        </div>
        <div class="grid" style="transform-origin: 0 0; transform: translateZ(-500px);">
            <div class="cell" v-for="_ in cells"><span></span></div>
        </div>
        <div class="grid" style="background: rgba(0, 255, 0, .2); transform-origin: 0 0; transform: translateX(500px) rotateY(90deg);">
            <div class="cell" v-for="_ in cells"><span></span></div>
        </div>
        <div class="grid" style="background: rgba(255, 0, 255, .2); transform-origin: 0 0; transform: rotateY(90deg);">
            <div class="cell" v-for="_ in cells"><span></span></div>
        </div>
        <div class="grid" style="background: rgba(0, 0, 255, .2); transform-origin: 0 0; transform: translateY(500px) rotateX(-90deg);">
            <div class="cell" v-for="_ in cells"><span></span></div>
        </div>
        <div class="grid" style="background: rgba(0, 255, 255, .2); transform-origin: 0 0; transform: rotateX(-90deg);">
            <div class="cell" v-for="_ in cells"><span></span></div>
        </div>

        <div class="base"></div>
        <div class="box source"></div>
        <div class="box target" :style="{ transform: `matrix(${a}, ${b}, ${c}, ${d}, ${tx}, ${ty})` }">target</div>
    </div>

    <div>
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

    </div>

    <div style="position: absolute; top: 0; right: 0; display: grid; justify-items: end;">
        <div class="control">
            <span>a1: {{ a1 }}</span>
            <input v-model="a1" type="range" min="-1" max="1" step="0.01" />
        </div>
        <div class="control">
            <span>b1: {{ b1 }}</span>
            <input v-model="b1" type="range" min="-1" max="1" step="0.01" />
        </div>
        <div class="control">
            <span>c1: {{ c1 }}</span>
            <input v-model="c1" type="range" min="-1" max="1" step="0.01" />
        </div>
        <div class="control">
            <span>d1: {{ d1 }}</span>
            <input v-model="d1" type="range" min="0" max="10" step="0.1" />
        </div>
        <div class="control">
            <span>a2: {{ a2 }}</span>
            <input v-model="a2" type="range" min="-1" max="1" step="0.01" />
        </div>
        <div class="control">
            <span>b2: {{ b2 }}</span>
            <input v-model="b2" type="range" min="-1" max="1" step="0.01" />
        </div>
        <div class="control">
            <span>c2: {{ c2 }}</span>
            <input v-model="c2" type="range" min="-1" max="1" step="0.01" />
        </div>
        <div class="control">
            <span>d2: {{ d2 }}</span>
            <input v-model="d2" type="range" min="0" max="10" step="0.1" />
        </div>
        <div class="control">
            <span>a3: {{ a3 }}</span>
            <input v-model="a3" type="range" min="-1" max="1" step="0.01" />
        </div>
        <div class="control">
            <span>b3: {{ b3 }}</span>
            <input v-model="b3" type="range" min="-1" max="1" step="0.01" />
        </div>
        <div class="control">
            <span>c3: {{ c3 }}</span>
            <input v-model="c3" type="range" min="-1" max="1" step="0.01" />
        </div>
        <div class="control">
            <span>d3: {{ d3 }}</span>
            <input v-model="d3" type="range" min="0" max="10" step="0.1" />
        </div>
        <div class="control">
            <span>a4: {{ a4 }}</span>
            <input v-model="a4" type="range" min="0" max="100" step="1" />
        </div>
        <div class="control">
            <span>b4: {{ b4 }}</span>
            <input v-model="b4" type="range" min="0" max="100" step="1" />
        </div>
        <div class="control">
            <span>c4: {{ c4 }}</span>
            <input v-model="c4" type="range" min="0" max="100" step="1" />
        </div>
        <div class="control">
            <span>d4: {{ d4 }}</span>
            <input v-model="d4" type="range" min="0" max="10" step="0.1" />
        </div>

        <div class="control">
            <span>x rotate: {{ xr }}</span>
            <input v-model="xr" type="range" min="0" max="360" step="1" @input="rotate" />
        </div>
        <div class="control">
            <span>y rotate: {{ yr }}</span>
            <input v-model="yr" type="range" min="0" max="360" step="1" @input="rotate" />
        </div>
        <div class="control">
            <span>z rotate: {{ zr }}</span>
            <input v-model="zr" type="range" min="0" max="360" step="1" @input="rotate" />
        </div>

    </div>

    <math style="position: absolute; left: 0; bottom: 0;">
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

    <math style="position: absolute; right: 0; bottom: 0;">
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

    <div style="position: absolute; bottom: 0; left: 0; right: 0; text-align: center;">
        <div>
            <span>matrix({{ a }}, {{ b }}, {{ c }}, {{ d }}, {{ tx }}, {{ ty }})</span>
            <button @click="reset('matrix')">reset</button>
        </div>
        <div>
            <span>matrix3d({{ a1 }}, {{ b1 }}, {{ c1 }}, {{ d1 }}, {{ a2 }}, {{ b2 }}, {{ c2 }}, {{ d2 }}, {{ a3 }}, {{
                b3 }}, {{ c3 }}, {{ d3 }},
                {{ a4 }}, {{ b4 }}, {{ c4 }}, {{ d4 }})</span>
            <button @click="reset('matrix3d')">reset</button>
        </div>
        <div>
            <button @click="animation">{{ isAnimating ? '暂停' : '癫狂' }}</button>
        </div>
    </div>
</template>

<script setup>
import { ref } from "vue";

const cells = 10 * 10;

const a = ref(1);
const b = ref(0);
const c = ref(0);
const d = ref(1);
const tx = ref(0);
const ty = ref(0);

const a1 = ref(1); const a2 = ref(0); const a3 = ref(0); const a4 = ref(0);
const b1 = ref(0); const b2 = ref(1); const b3 = ref(0); const b4 = ref(0);
const c1 = ref(0); const c2 = ref(0); const c3 = ref(1); const c4 = ref(0);
const d1 = ref(0); const d2 = ref(0); const d3 = ref(0); const d4 = ref(1);

const xr = ref(0);
const yr = ref(0);
const zr = ref(0);

const rotate = () => {
    const [
        a, b, c, d,
        e, f, g, h,
        i, j, k, l,
        m, n, o, p,
    ] = rotationMatrixXYZ(xr.value, yr.value, zr.value)
    a1.value = a;
    b1.value = b;
    c1.value = c;
    d1.value = d;
    a2.value = e;
    b2.value = f;
    c2.value = g;
    d2.value = h;
    a3.value = i;
    b3.value = j;
    c3.value = k;
    d3.value = l;
    a4.value = m;
    b4.value = n;
    c4.value = o;
    d4.value = p;
}

const reset = (name) => {
    switch (name) {
        case 'matrix': {
            a.value = 1;
            b.value = 0;
            c.value = 0;
            d.value = 1;
            tx.value = 0;
            ty.value = 0;
            break;
        };
        case 'matrix3d': {
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

            xr.value = 0;
            yr.value = 0;
            zr.value = 0;
            break;
        };
        default: break;
    }
}


function degreesToRadians(degrees) {
    return degrees * (Math.PI / 180);
}

function rotationMatrixXYZ(degreesX, degreesY, degreesZ) {
    const radX = degreesToRadians(degreesX);
    const radY = degreesToRadians(degreesY);
    const radZ = degreesToRadians(degreesZ);

    const cosX = Math.cos(radX);
    const sinX = Math.sin(radX);
    const cosY = Math.cos(radY);
    const sinY = Math.sin(radY);
    const cosZ = Math.cos(radZ);
    const sinZ = Math.sin(radZ);

    const Rx = [
        1, 0, 0, 0,
        0, cosX, -sinX, 0,
        0, sinX, cosX, 0,
        0, 0, 0, 1
    ];

    const Ry = [
        cosY, 0, sinY, 0,
        0, 1, 0, 0,
        -sinY, 0, cosY, 0,
        0, 0, 0, 1
    ];

    const Rz = [
        cosZ, -sinZ, 0, 0,
        sinZ, cosZ, 0, 0,
        0, 0, 1, 0,
        0, 0, 0, 1
    ];

    return multiplyMatrices(multiplyMatrices(Rz, Ry), Rx).map((num) => num.toFixed(2));
}

function multiplyMatrices(A, B) {
    const result = [];
    for (let i = 0; i < 4; i++) {
        result[i] = [];
        for (let j = 0; j < 4; j++) {
            result[i][j] = A[i * 4] * B[j] +
                A[i * 4 + 1] * B[j + 4] +
                A[i * 4 + 2] * B[j + 8] +
                A[i * 4 + 3] * B[j + 12];
        }
    }
    return result.flat();
}

const isAnimating = ref(false);
let timeoutId;

function getRandomAngle() {
    return Math.floor(Math.random() * 361);
}

const animate = () => {
    if (!isAnimating.value) return;

    xr.value = getRandomAngle();
    yr.value = getRandomAngle();
    zr.value = getRandomAngle();
    rotate();

    timeoutId = setTimeout(animate, 300);
};

const startAnimation = () => {
    if (!isAnimating.value) {
        isAnimating.value = true;
        animate();
    }
};

const stopAnimation = () => {
    isAnimating.value = false;
    clearTimeout(timeoutId);
};

const animation = () => {
    if (isAnimating.value) {
        stopAnimation();
    } else {
        startAnimation();
    }
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
    transform-style: preserve-3d;
    transition: all .6s;
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
    grid-template-columns: 1fr 1fr;
}

input {
    cursor: grab;
}

input:active {
    cursor: grabbing;
}
</style>