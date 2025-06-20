<template>
    <div class="px-8 py-2 rounded-box">
        <div class="flex flex-col gap-3">
            <div class="flex flex-col gap-1">
                <span class="progress-label ms-[calc(100%-1.25rem)] 
                bg-primary/30 text-primary-content/50 border-0">100%</span>
                <div class="progress h-1.5" role="progressbar" aria-label="100% Progressbar" aria-valuenow="100"
                    aria-valuemin="0" aria-valuemax="100">
                    <div class="progress-bar progress-primary w-100/100 opacity-50"></div>
                </div>
            </div>
        </div>
    </div>
</template>