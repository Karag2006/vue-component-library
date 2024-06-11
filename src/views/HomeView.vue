<script setup>
import SectionWrapper from '@/components/wrapper/SectionWrapper.vue'
import ComponentGrid from '@/components/wrapper/ComponentGrid.vue'
import ComponentView from '@/components/wrapper/ComponentView.vue'
import CustomButton from '@/components/CustomButton.vue'
import ScrollContainer from '@/components/ScrollContainer.vue'
</script>

<template>
    <main>
        <SectionWrapper class="buttons">
            <template #SectionName>Buttons</template>
            <ComponentGrid>
                <ComponentView>
                    <CustomButton variant="outline" size="md">
                        Button
                    </CustomButton>
                </ComponentView>
                <ComponentView> </ComponentView>
                <ComponentView>
                    <CustomButton variant="outline" size="md">
                        Button
                    </CustomButton>
                </ComponentView>
                <ComponentView>
                    <CustomButton variant="outline" size="md">
                        Button
                    </CustomButton>
                </ComponentView>
            </ComponentGrid>
        </SectionWrapper>
        <SectionWrapper class="display-elements">
            <template #SectionName>Display Elements</template>
            <ComponentGrid>
                <ComponentView>
                    <ScrollContainer />
                </ComponentView>
            </ComponentGrid>
        </SectionWrapper>
    </main>
</template>
