Bouton style

    .lf-wcag-contrast {
        display: inline-flex;
        align-items: center;
        
        &__switch {
            display: inline-flex;
            position: relative;
            margin-right: $gutter-xs;
            border-radius: 12px;
            background: $bg-color;
            width: 24px;
            height: 12px;
    
            &::before {
                position: absolute;
                top: 0;
                left: 0;
                transition: $transition-default;
                margin: 2px;
                border-radius: 5px;
                background: $text-color;
                width: 8px;
                height: 8px;
                content: '';
            }
        }
    
        &__label {
            &__on {
                display: none;
            }
    
            &__off {
                display: inline-flex;
            }
        }
    
        &.lf-wcag-contrasted & {
            &__switch {
                &::before {
                    left: calc(100% - 12px);
                }
            }
    
            &__label {
                &__on {
                    display: inline-flex;
                }
    
                &__off {
                    display: none;
                }
            }
        }
    }
