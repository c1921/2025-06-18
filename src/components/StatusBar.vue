<template>
    <div class="bg-base-100 px-6 py-2 grid grid-cols-2 gap-8 rounded-box">
        <div class="flex flex-col gap-3">
            <div class="flex flex-col gap-1">
                <span class="progress-label ms-[calc(0%-1.25rem)]">0%</span>
                <div class="progress h-2" role="progressbar" aria-label="25% Progressbar" aria-valuenow="25"
                    aria-valuemin="0" aria-valuemax="100">
                    <div class="progress-bar progress-primary w-0/100"></div>
                </div>
            </div>
            <div class="progress w-3/5" role="progressbar" aria-label="25% Progressbar" aria-valuenow="25"
                aria-valuemin="0" aria-valuemax="100">
                <div class="progress-bar progress-warning w-1/4"></div>
            </div>

        </div>

        <div class="flex flex-col gap-3 rotate-y-180">
            <div class="flex flex-col gap-1">
                <span class="progress-label ms-[calc(100%-1.25rem)] rotate-y-180">100%</span>
                <div class="progress h-2" role="progressbar" aria-label="25% Progressbar" aria-valuenow="25"
                    aria-valuemin="0" aria-valuemax="100">
                    <div class="progress-bar progress-primary w-100/100"></div>
                </div>
            </div>
            <div class="progress w-3/5" role="progressbar" aria-label="25% Progressbar" aria-valuenow="25"
                aria-valuemin="0" aria-valuemax="100">
                <div class="progress-bar progress-warning w-1/4"></div>
            </div>

        </div>
    </div>
</template>