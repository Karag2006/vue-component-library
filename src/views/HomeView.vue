<script setup>
import SectionWrapper from '@/components/wrapper/SectionWrapper.vue'
import ComponentGrid from '@/components/wrapper/ComponentGrid.vue'
import DisplayCard from '@/components/wrapper/DisplayCard.vue'
import CustomButton from '@/components/CustomButton.vue'
import ScrollContainer from '@/components/ScrollContainer.vue'
</script>

<template>
    <main>
        <SectionWrapper class="buttons">
            <template #SectionName>Buttons</template>
            <ComponentGrid>
                <DisplayCard>
                    <template #header> Custom Button </template>
                    <CustomButton variant="outline" size="md">
                        Button
                    </CustomButton>
                    <template #footer>
                        Inspired by shadcn-ui. uses 'variant' and 'size' custom
                        properties to choose between predefined button
                        layouts.</template
                    >
                </DisplayCard>
            </ComponentGrid>
        </SectionWrapper>
        <SectionWrapper class="display-elements">
            <template #SectionName>Display Elements</template>
            <ComponentGrid>
                <DisplayCard>
                    <template #header> Scroll Container </template>
                    <ScrollContainer />
                    <template #footer>
                        requires height or max-height to be set on the parent.
                        Scroll is limited to the container and can't "spill"
                        into surrounding elements
                    </template>
                </DisplayCard>
            </ComponentGrid>
        </SectionWrapper>
    </main>
</template>
